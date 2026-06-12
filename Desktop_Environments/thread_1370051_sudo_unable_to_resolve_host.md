---
title: "sudo: unable to resolve host"
date: 2010-01-01
forum: Desktop Environments
---

### Post by juanchito2006 on 2010-01-01
Recently I've found this warning after executing commands as a superuser (e.g. sudo aptitude, sudo nano). The commands run properly, but the warning wasn't present before.

My /etc/hosts file is as follows:

```

127.0.0.1       localhost
127.0.1.1       wolf

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And my hostname is effectively wolf. I've looked at various solutions at the forums but they seem futile. Any ideas? I'm running Karmic.

---

### Post by Barriehie on 2010-01-01
> **juanchito2006 said:**
> Recently I've found this warning after executing commands as a superuser (e.g. sudo aptitude, sudo nano). The commands run properly, but the warning wasn't present before.

My /etc/hosts file is as follows:

```

127.0.0.1       localhost
127.0.1.1       wolf

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And my hostname is effectively wolf. I've looked at various solutions at the forums but they seem futile. Any ideas? I'm running Karmic.

Are they mapped to different ports?  What do you have in your /etc/apache2/sites-enabled directory?

---

### Post by juanchito2006 on 2010-01-01
How do I know if they're mapped?

Anyway, the only file in /etc/apache2/sites-enabled is 000-default.

The contents of the file are:

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by Barriehie on 2010-01-01
On my machine I've got dyndns pointing requests to myip:45826 and localhost is port 80.  So in my /etc/apache2/sites-enabled I've got localhost.conf and ubuntubox.hobby-site.org.conf.

localhost.conf
```

<VirtualHost *:80>
	ServerName localhost
	ServerAdmin barrie@localhost
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

ubuntubox.hobby-site.org.conf
```

<VirtualHost *:45826>
	ServerName ubuntubox.hobby-site.org
	ServerAdmin barrie@localhost
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

/etc/ports.conf
```

Listen 80
Listen 45826

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

HTH!

---

### Post by Barriehie on 2010-01-01
Also, the .conf files in /etc/apache2/sites-enabled/ are/should be symlinks to the files in /etc/apache2/sites-available.  This is so that if you've got multiple sites on one machine it makes mgmt. easier.

---

### Post by juanchito2006 on 2010-01-01
In /etc/apache2/sites-available/ I have default and default-ssl.

My default is:

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

My default-ssl is:

```

<IfModule mod_ssl.c>
<VirtualHost _default_:443>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/ssl_access.log combined

	Alias /doc/ "/usr/share/doc/"
	<Directory "/usr/share/doc/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order deny,allow
		Deny from all
		Allow from 127.0.0.0/255.0.0.0 ::1/128
	</Directory>

	#   SSL Engine Switch:
	#   Enable/Disable SSL for this virtual host.
	SSLEngine on

	#   A self-signed (snakeoil) certificate can be created by installing
	#   the ssl-cert package. See
	#   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
	#   If both key and certificate are stored in the same file, only the
	#   SSLCertificateFile directive is needed.
	SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
	SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

	#   Server Certificate Chain:
	#   Point SSLCertificateChainFile at a file containing the
	#   concatenation of PEM encoded CA certificates which form the
	#   certificate chain for the server certificate. Alternatively
	#   the referenced file can be the same as SSLCertificateFile
	#   when the CA certificates are directly appended to the server
	#   certificate for convinience.
	#SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt

	#   Certificate Authority (CA):
	#   Set the CA certificate verification path where to find CA
	#   certificates for client authentication or alternatively one
	#   huge file containing all of them (file must be PEM encoded)
	#   Note: Inside SSLCACertificatePath you need hash symlinks
	#         to point to the certificate files. Use the provided
	#         Makefile to update the hash symlinks after changes.
	#SSLCACertificatePath /etc/ssl/certs/
	#SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt

	#   Certificate Revocation Lists (CRL):
	#   Set the CA revocation path where to find CA CRLs for client
	#   authentication or alternatively one huge file containing all
	#   of them (file must be PEM encoded)
	#   Note: Inside SSLCARevocationPath you need hash symlinks
	#         to point to the certificate files. Use the provided
	#         Makefile to update the hash symlinks after changes.
	#SSLCARevocationPath /etc/apache2/ssl.crl/
	#SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

	#   Client Authentication (Type):
	#   Client certificate verification type and depth.  Types are
	#   none, optional, require and optional_no_ca.  Depth is a
	#   number which specifies how deeply to verify the certificate
	#   issuer chain before deciding the certificate is not valid.
	#SSLVerifyClient require
	#SSLVerifyDepth  10

	#   Access Control:
	#   With SSLRequire you can do per-directory access control based
	#   on arbitrary complex boolean expressions containing server
	#   variable checks and other lookup directives.  The syntax is a
	#   mixture between C and Perl.  See the mod_ssl documentation
	#   for more details.
	#<Location />
	#SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
	#            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
	#            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
	#            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
	#            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
	#           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
	#</Location>

	#   SSL Engine Options:
	#   Set various options for the SSL engine.
	#   o FakeBasicAuth:
	#     Translate the client X.509 into a Basic Authorisation.  This means that
	#     the standard Auth/DBMAuth methods can be used for access control.  The
	#     user name is the `one line' version of the client's X.509 certificate.
	#     Note that no password is obtained from the user. Every entry in the user
	#     file needs this password: `xxj31ZMTZzkVA'.
	#   o ExportCertData:
	#     This exports two additional environment variables: SSL_CLIENT_CERT and
	#     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
	#     server (always existing) and the client (only existing when client
	#     authentication is used). This can be used to import the certificates
	#     into CGI scripts.
	#   o StdEnvVars:
	#     This exports the standard SSL/TLS related `SSL_*' environment variables.
	#     Per default this exportation is switched off for performance reasons,
	#     because the extraction step is an expensive operation and is usually
	#     useless for serving static content. So one usually enables the
	#     exportation for CGI and SSI requests only.
	#   o StrictRequire:
	#     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
	#     under a "Satisfy any" situation, i.e. when it applies access is denied
	#     and no other module can change it.
	#   o OptRenegotiate:
	#     This enables optimized SSL connection renegotiation handling when SSL
	#     directives are used in per-directory context.
	#SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
	<FilesMatch "\.(cgi|shtml|phtml|php)$">
		SSLOptions +StdEnvVars
	</FilesMatch>
	<Directory /usr/lib/cgi-bin>
		SSLOptions +StdEnvVars
	</Directory>

	#   SSL Protocol Adjustments:
	#   The safe and default but still SSL/TLS standard compliant shutdown
	#   approach is that mod_ssl sends the close notify alert but doesn't wait for
	#   the close notify alert from client. When you need a different shutdown
	#   approach you can use one of the following variables:
	#   o ssl-unclean-shutdown:
	#     This forces an unclean shutdown when the connection is closed, i.e. no
	#     SSL close notify alert is send or allowed to received.  This violates
	#     the SSL/TLS standard but is needed for some brain-dead browsers. Use
	#     this when you receive I/O errors because of the standard approach where
	#     mod_ssl sends the close notify alert.
	#   o ssl-accurate-shutdown:
	#     This forces an accurate shutdown when the connection is closed, i.e. a
	#     SSL close notify alert is send and mod_ssl waits for the close notify
	#     alert of the client. This is 100% SSL/TLS standard compliant, but in
	#     practice often causes hanging connections with brain-dead browsers. Use
	#     this only for browsers where you know that their SSL implementation
	#     works correctly.
	#   Notice: Most problems of broken clients are also related to the HTTP
	#   keep-alive facility, so you usually additionally want to disable
	#   keep-alive for those clients, too. Use variable "nokeepalive" for this.
	#   Similarly, one has to force some clients to use HTTP/1.0 to workaround
	#   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
	#   "force-response-1.0" for this.
	BrowserMatch ".*MSIE.*" \
		nokeepalive ssl-unclean-shutdown \
		downgrade-1.0 force-response-1.0

</VirtualHost>
</IfModule>

```

So, what do you suggest I should do?

---

### Post by Barriehie on 2010-01-01
Are you using dyndns or some such service to provide an actual redirection to your machine?  You at least should have a localhost.conf file.
```

<VirtualHost *:80>
	ServerName localhost
	ServerAdmin **YourEmailAddress**
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

/etc/ports.conf
```

Listen 80
Listen **port for 127.0.1.1**

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

With those files in place you should be able to:
```

sudo /etc/init.d/apache2 restart
``` and then point your browser to [http://localhost/](http://localhost/) and you'll see the default page; i.e. 'It Works'

Edit: When you've got the localhost.conf file in place rename the default.conf file to default.conf.bak   You can leave the SSL file alone.

---

### Post by juanchito2006 on 2010-01-02
My output for sudo /etc/init.d/apache2 restart was:

```

$ sudo /etc/init.d/apache2 restart
sudo: unable to resolve host wolf
 * Restarting web server apache2                                                apache2: apr_sockaddr_info_get() failed for wolf
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting .apache2: apr_sockaddr_info_get() failed for wolf
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

```

Should I write the localhost.conf file to which folder, sites-enabled or sites-available? I wrote it to sites-enabled.

[http://localhost/](http://localhost/) successfully sends me to the "It works!"  page, though it worked before. I'm still having this sudo warning.

---

### Post by Barriehie on 2010-01-02
> **juanchito2006 said:**
> My output for sudo /etc/init.d/apache2 restart was:

```

$ sudo /etc/init.d/apache2 restart
sudo: unable to resolve host wolf
 * Restarting web server apache2                                                apache2: apr_sockaddr_info_get() failed for wolf
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting .apache2: apr_sockaddr_info_get() failed for wolf
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

```

Should I write the localhost.conf file to which folder, sites-enabled or sites-available? I wrote it to sites-enabled.

[http://localhost/](http://localhost/) successfully sends me to the "It works!"  page, though it worked before. I'm still having this sudo warning.

It worked, you don't have a wolf.conf file so that's why it can't resolve it.  You also need a /etc/hostname file that names the servers fully qualified domain name, FQDN.  It was able to resolve localhost that's why it's using it for the ServerName.  To resolve 'wolf' you'll need to assign it another port and then wolf.conf will look like localhost.conf EXCEPT for the port number that you're using and UNLESS you're using something like dyndns to redirect requests for 'wolf' to your machine.

HTH,

---

### Post by juanchito2006 on 2010-01-02
I'm not sure what to do, I'm really a novice in this stuff. Would you give me step by step directions in order to resolve my computer host?

---

### Post by Barriehie on 2010-01-02
> **juanchito2006 said:**
> I'm not sure what to do, I'm really a novice in this stuff. Would you give me step by step directions in order to resolve my computer host?

Your best bet would be to start [[color="blue"]here[/color]](https://help.ubuntu.com/9.10/serverguide/C/web-servers.html).

---

### Post by Fibonacci on 2010-01-02
I've checked on my machine.
The files on /etc/apache2/sites-enabled and /etc/apache2/sites-available are identical to the OP's (/etc/apache2/sites-enabled/000-default is a symlink to /etc/apache2/sites-available/default by the way, so check it's the same for you).
/etc/hostname contains just one line - my hostname.
None of the other files that were mentioned exist on my machine, including /etc/ports.conf, /etc/apache2/sites-enabled/localhost.conf, and so on and so forth.
When restarting Apache I get exactly the same message as the OP:
```
$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                        [ OK ]

```

Yet I don't get the same error message he does upon running sudo, so I don't think it's related to the aforementioned files.

---

### Post by juanchito2006 on 2010-01-03
I'm having a return value EAI_NONAME on getaddrinfo over localhost and wolf, normal systems ought to return a value of 0. So, how can I determine de cause of this problem?

The program I used to return this value was:

```

#include <stdio.h>
#include <stddef.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>

int main(void)
{
struct addrinfo *result;
int i=getaddrinfo("wolf", NULL, NULL, &result);
printf("%s\n",(i==EAI_NONAME)?"EAI_NONAME":"unknown code");
return 0;
}

```

With any other valid host, there's no EAI_NONAME output.

---

### Post by Barriehie on 2010-01-03
> **Fibonacci said:**
> I've checked on my machine.
The files on /etc/apache2/sites-enabled and /etc/apache2/sites-available are identical to the OP's (/etc/apache2/sites-enabled/000-default is a symlink to /etc/apache2/sites-available/default by the way, so check it's the same for you).
/etc/hostname contains just one line - my hostname.
None of the other files that were mentioned exist on my machine, including /etc/ports.conf, /etc/apache2/sites-enabled/localhost.conf, and so on and so forth.
When restarting Apache I get exactly the same message as the OP:
```
$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                        [ OK ]

```

Yet I don't get the same error message he does upon running sudo, so I don't think it's related to the aforementioned files.

Can't remember what tutorial I used or if I just read through the apache2 docs but this is what happens when I restart my apache2.
```

$ >> sudo /etc/init.d/apache2 restart
[sudo] password for barrie: 
 * Restarting web server apache2                                                    [ OK ] 
05:12:15 /home/barrie $ >> 
```

---

### Post by Fibonacci on 2010-01-03
> **Barriehie said:**
> Can't remember what tutorial I used or if I just read through the apache2 docs but this is what happens when I restart my apache2.
```

$ >> sudo /etc/init.d/apache2 restart
[sudo] password for barrie: 
 * Restarting web server apache2                                                    [ OK ] 
05:12:15 /home/barrie $ >> 
```

So you don't get any message about sudo being unable to resolve any host - neither do I, so I doubt it's related to Apache.

> **juanchito2006 said:**
> I'm having a return value EAI_NONAME on getaddrinfo over localhost and wolf, normal systems ought to return a value of 0. So, how can I determine de cause of this problem?

The program I used to return this value was:

```

#include <stdio.h>
#include <stddef.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>

int main(void)
{
struct addrinfo *result;
int i=getaddrinfo("wolf", NULL, NULL, &result);
printf("%s\n",(i==EAI_NONAME)?"EAI_NONAME":"unknown code");
return 0;
}

```

With any other valid host, there's no EAI_NONAME output.

Also, getaddrinfo("localhost",NULL,NULL,&result) returns 0 for me, and the same holds if I replace "localhost" with my hostname.

---

### Post by Barriehie on 2010-01-03
> **Fibonacci said:**
> So you don't get any message about sudo being unable to resolve any host - neither do I, so I doubt it's related to Apache.

Apache is the package that has to resolve the hostname per the /etc/hostname file and a corresponding .conf file.

---

### Post by Fibonacci on 2010-01-03
> **Barriehie said:**
> Apache is the package that has to resolve the hostname per the /etc/hostname file and a corresponding .conf file.

I thought all sudo did was call getaddrinfo to resolve it.

---

### Post by Barriehie on 2010-01-03
> **Fibonacci said:**
> I thought all sudo did was call getaddrinfo to resolve it.

sudo allows you to run a command as root/SuperUser; think of it as **s**uper**u**ser**do**.  sudo by itself returns a usage example.  If your machine has an /etc/hostname file then the contents of that file is read into the global variable, $HOSTNAME, and if you're running apache it has to find a .conf file to define the 'map' of that host.  Where it's root directory is, is it port mapped or IP based, blah blah blah :)  Many of those things also depend on other files.  I'm not a network expert! it took me a week to get mine going to where I don't have any errors or warnings!

---

### Post by Fibonacci on 2010-01-03
> **Barriehie said:**
> sudo allows you to run a command as root/SuperUser; think of it as **s**uper**u**ser**do**.  sudo by itself returns a usage example.  If your machine has an /etc/hostname file then the contents of that file is read into the global variable, $HOSTNAME, and if you're running apache it has to find a .conf file to define the 'map' of that host.  Where it's root directory is, is it port mapped or IP based, blah blah blah :)  Many of those things also depend on other files.  I'm not a network expert! it took me a week to get mine going to where I don't have any errors or warnings!

I know what sudo is, but that doesn't contradict what I said about it using getaddrinfo.
Moreover, it doesn't answer why I have an identical Apache configuration as the OP, yet I don't get the same error messages.

---

### Post by Barriehie on 2010-01-03
> **Fibonacci said:**
> I know what sudo is, but that doesn't contradict what I said about it using getaddrinfo.
Moreover, it doesn't answer why I have an identical Apache configuration as the OP, yet I don't get the same error messages.

getaddrinfo has a gai.conf file in /etc.  Perhaps they're the same.  Unless, you, or a package, has changed it the default install is a commented out file.

---

### Post by Fibonacci on 2010-01-03
> **Barriehie said:**
> getaddrinfo has a gai.conf file in /etc.  Perhaps they're the same.  Unless, you, or a package, has changed it the default install is a commented out file.

It is for me, let's see if it is also for the OP.

---

### Post by Barriehie on 2010-01-04
OP, been messing around and here's what I've done.

/etc/hosts
```

# The following lines are desirable for IPv6 capable hosts
#

#
#		My Setup
#
# IP      Hostname              Alias
#
127.0.0.1 localhost             localhost
127.0.1.1 localhost             barriehie


::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Then shut down completely and powered back up.  I've found many links on the web to say just restart your network services but that didn't work!

Now look at the attached screenshot.  Try editing your /etc/hosts the same way and see if that fixes it.

---

### Post by juanchito2006 on 2010-01-04
I modified my /etc/hosts like this:

```

127.0.0.1       localhost       localhost
127.0.1.1       localhost       wolf

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The issue persists.

---

### Post by Fibonacci on 2010-01-04
I just tried it on a fresh install which does not contain Apache, and the results are the same as on my main machine (except, of course, that the files I mentioned which are related to Apache do not exist at all), proving once and for all that the issue is unrelated to Apache.

Indeed the whole reason sudo cannot resolve his hostname is getaddrinfo. As for what could be making getaddrinfo return EAI_NONAME when looking for localhost, I don't know.

I've heard somewhere that some SAMBA packages replace getaddrinfo with their own version. Perhaps that could be part of the problem?

---

### Post by Barriehie on 2010-01-04
It's a bug. See [[color="blue"]here[/color]](http://ubuntuforums.org/showthread.php?t=1303356&highlight=resolve+hostname).

---

### Post by juanchito2006 on 2010-02-02
Already fixed this issue, it had nothing to do with Apache. For some reason, /etc/nsswitch.conf went missing. Restoring it fixed the issue.

---

