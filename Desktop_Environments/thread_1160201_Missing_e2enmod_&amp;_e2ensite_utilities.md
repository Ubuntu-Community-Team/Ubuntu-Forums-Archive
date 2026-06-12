---
title: "Missing e2enmod &amp; e2ensite utilities"
date: 2009-05-15
forum: Desktop Environments
---

### Post by slipstream180 on 2009-05-15
Hi all - I am using the desktop version of 9.04. I am trying to set up Apache for SSL. However, as the Apache Doc page ([https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)) recommends using the e2enmod & e2ensite to facilitate configuration, I can't seem to find it on my machine...

I've tried:
> find -name e2enmod

from root & it comes up empty. (Just in case it's sitting outside my path somewhere)

I've also tried 
> sudo apt-get upgrade apache2-common 

which comes back with something about apache2-common being deprecated to apache2.2.-common. If I try apache2.2.-common it says there's nothing to update.

Scanning the standard search engines seems to come up empty for these two binaries...

Any ideas as to how to get these helpful utilities, or some apt-get commands to debug our way to a full installation?

Thanks in advance, for any ideas/help.

Cheers.

---

### Post by slipstream180 on 2009-05-15
OK. A little more info...using aptitude at the prompt > aptitude search apache2. This provides a list of relevant apache submodules and their status in the installation:

```
i A apache2                         - Apache HTTP Server metapackage            
v   apache2-dev                     -                                           
p   apache2-doc                     - Apache HTTP Server documentation          
v   apache2-mpm                     -                                           
p   apache2-mpm-event               - Apache HTTP Server - event driven model   
p   apache2-mpm-itk                 - multiuser MPM for Apache 2.2              
i A apache2-mpm-prefork             - Apache HTTP Server - traditional non-threa
p   apache2-mpm-worker              - Apache HTTP Server - high speed threaded m
p   apache2-prefork-dev             - Apache development headers - non-threaded 
p   apache2-src                     - Apache source code                        
p   apache2-suexec                  - Standard suexec program for Apache 2 mod_s
p   apache2-suexec-custom           - Configurable suexec program for Apache 2 m
p   apache2-threaded-dev            - Apache development headers - threaded MPM 
i   apache2-utils                   - utility programs for webservers           
i   apache2.2-common                - Apache HTTP Server common files           
p   gforge-web-apache2              - collaborative development tool - web part 
p   libapache2-authcassimple-perl   - Apache2 module to authentificate trough a 
p   libapache2-authenntlm-perl      - Perform Microsoft NTLM and Basic User Auth
p   libapache2-mod-apparmor         - changehat AppArmor library as an Apache mo
p   libapache2-mod-apreq2           - generic Apache request library - Apache mo
p   libapache2-mod-auth-kerb        - apache2 module for Kerberos authentication
p   libapache2-mod-auth-mysql       - Apache 2 module for MySQL authentication  
p   libapache2-mod-auth-openid      - OpenID authentication module for Apache2  
p   libapache2-mod-auth-pam         - module for Apache2 which authenticate usin
p   libapache2-mod-auth-pgsql       - Module for Apache2 which provides pgsql au
p   libapache2-mod-auth-plain       - Module for Apache2 which provides plaintex
p   libapache2-mod-auth-radius      - Apache 2.x module for RADIUS authenticatio
p   libapache2-mod-auth-sys-group   - Module for Apache2 which checks user again
p   libapache2-mod-authn-sasl       - SASL authentication backend provider for A
p   libapache2-mod-authnz-external  - authenticate Apache against external authe
p   libapache2-mod-axis2c           - Apache web services engine - apache module
p   libapache2-mod-bt               - BitTorrent tracker for the Apache2 web ser
p   libapache2-mod-bt-dev           - Header files for mod_bt                   
p   libapache2-mod-bw               - bandwidth limiting module for apache2     
p   libapache2-mod-chroot           - run Apache in a secure chroot environment 
p   libapache2-mod-defensible       - module for Apache2 which provides DNSBL us
p   libapache2-mod-dnssd            - Zeroconf support for Apache 2 via avahi   
p   libapache2-mod-encoding         - Apache2 module for non-ascii filename inte
p   libapache2-mod-evasive          - evasive module to minimize HTTP DoS or bru
p   libapache2-mod-fastcgi          - Apache 2 FastCGI module for long-running C
p   libapache2-mod-fcgid            - an alternative module compat with mod_fast
p   libapache2-mod-geoip            - GeoIP support for apache2                 
p   libapache2-mod-gnutls           - Apache2 module for SSL and TLS encryption 
p   libapache2-mod-jk               - Apache 2 connector for the Tomcat Java ser
p   libapache2-mod-layout           - Apache web page content wrapper           
p   libapache2-mod-ldap-userdir     - Apache module that provides UserDir lookup
p   libapache2-mod-line-edit        - search-and-replace line editor module for 
p   libapache2-mod-lisp             - An Apache2 module that interfaces with Lis
p   libapache2-mod-log-sql          - Use SQL to store/write your apache queries
p   libapache2-mod-log-sql-dbi      - Use SQL to store/write your apache queries
p   libapache2-mod-log-sql-mysql    - Use SQL to store/write your apache queries
p   libapache2-mod-log-sql-ssl      - Use SQL to store/write your apache queries
p   libapache2-mod-macro            - Create macros inside apache2 config files 
p   libapache2-mod-mime-xattr       - Apache2 module to get MIME info from files
p   libapache2-mod-mono             - Apache module for running ASP.NET applicat
p   libapache2-mod-musicindex       - Browse, stream, download and search throug
p   libapache2-mod-neko             - Apache module for running server-side neko
p   libapache2-mod-ocamlnet         - OCaml application-level Internet libraries
p   libapache2-mod-passenger        - Rails and Rack support for Apache2        
p   libapache2-mod-perl2            - Integration of perl with the Apache2 web s
p   libapache2-mod-perl2-dev        - Integration of perl with the Apache2 web s
p   libapache2-mod-perl2-doc        - Integration of perl with the Apache2 web s
i A libapache2-mod-php5             - server-side, HTML-embedded scripting langu
p   libapache2-mod-php5filter       - server-side, HTML-embedded scripting langu
p   libapache2-mod-proxy-html       - Apache2 filter module for HTML links rewri
p   libapache2-mod-python           - Python-embedding module for Apache 2      
p   libapache2-mod-python-doc       - Python-embedding module for Apache 2 - doc
v   libapache2-mod-python2.6        -                                           
p   libapache2-mod-random           - Create random ads, quotes and redirects   
p   libapache2-mod-removeip         - Module to remove IP from apache2's logs   
p   libapache2-mod-rpaf             - module for Apache2 which takes the last IP
p   libapache2-mod-ruby             - Embedding Ruby in the Apache2 web server  
p   libapache2-mod-scgi             - Apache module implementing the SCGI protoc
v   libapache2-mod-security2        -                                           
p   libapache2-mod-shib             - Federated web single sign-on system (Apach
p   libapache2-mod-spamhaus         - Apache DNSBL module that blocks listed IP 
p   libapache2-mod-speedycgi        - apache2 module to speed up perl scripts by
p   libapache2-mod-suphp            - Apache2 module to run php scripts with the
p   libapache2-mod-vhost-hash-alias - Fast and efficient way to manage virtual h
p   libapache2-mod-vhost-ldap       - Apache 2 module for Virtual Hosting from L
p   libapache2-mod-wsgi             - Python WSGI adapter module for Apache     
p   libapache2-modbt-perl           - Perl bindings for mod_bt                  
p   libapache2-modxslt              - XSLT processing module for Apache 2.x base
p   libapache2-redirtoservname      - Apache 2 module to redirect users to the c
p   libapache2-reload-perl          - Reload Perl modules when changed on disk  
p   libapache2-request-perl         - generic Apache request library - Perl modu
p   libapache2-svn                  - Subversion server modules for Apache      
p   libapache2-webauth              - Apache 2 modules for WebAuth authenticatio
p   libapache2-webkdc               - Apache 2 modules for a WebAuth authenticat
p   mahara-apache2                  - Electronic portfolio, weblog, and resume b
p   php5-apache2-mod-bt             - PHP bindings for mod_bt                   
p   rt3.6-apache2                   - Apache 2 specific files for request-tracke
p   torrus-apache2                  - Universal front-end for Round-Robin Databa

```

left-most column (i) indicates an installed package. 

So we have the following modules installed: 
apache2
apache2-mpm-prefork
apache2-utils (this is sort of where I'd expect e2enmod & e2ensite to be...)
apache2.2-common

These all look like the right packages to have...I'm beginning to suspect that d2enmod & e2ensite aren't distributed for the desktop...

---

### Post by slipstream180 on 2009-05-15
Problem solved. It's not e2enmod, it's **a**2ensite...my bad. a2ensite present and accounted for.

---

