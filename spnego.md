# Using SPNEGO in clj-http

SPNEGO (kerberos) support is available in clj-http. To use it

>
>(ns test
>  (:require [clj-http.client :as client]))
>
>  (client/get "http://some-kerberos.enabled.site.com" {:spnego-auth true})
>

On a Unix box adding the following jvm-opts will likely help you a kerberos
setup that is more usable than the base java kerberos bits.

>
>  :jvm-opts ["-Dsun.security.jgss.native=true"
>             "-Dsun.security.krb5.debug=true"
>             "-Djavax.security.auth.useSubjectCredsOnly=false"]
>
>

On a windows host you will need to have a krb5.conf defined. Some pointers to
how to get that going are here:
http://hc.apache.org/httpcomponents-client-ga/tutorial/html/authentication.html.


