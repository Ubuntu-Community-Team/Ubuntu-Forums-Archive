---
title: "Apache2 won't start, undefined symbol apr_ldap_ssl_init"
date: 2009-01-03
forum: General Help
---

### Post by Eviola on 2009-01-03
Hi everyone, I hope you can help with a problem I have been having...

I installed 8.10 not too long ago on an older machine which was previously running 8.04. This was a clean install as the previous system was a bit of a mess and I wanted to start over. While everything is fine for the most part, I can't seem to get Apache to start (it used to run fine in 8.04). Whenever I run either /etc/init.d/apache2 start or any form of apache2ctl command I get the following message:

>  * Starting web server apache2
/usr/sbin/apache2: symbol lookup error: /usr/sbin/apache2: undefined symbol: apr_ldap_ssl_init
[fail]

Naturally I have Googled this, and come up with a few results, including reinstalling Apache, reinstalling libapr and libaprutils, correcting some symlinks, changing configurations, disabling modules and installing extra packages... However the problem still persists and I can't seem to get rid of it :(

I installed apache2 via apt-get with no modules other than those enabled by default, if that helps. I am also running Kubuntu rather than Ubuntu.

Anyone have any ideas? Thanks in advance.

---

### Post by RealPSL on 2009-01-04
As far as I can tell that shared object comes from mod_ldap "/usr/lib/apache2/modules/mod_ldap.so". Are you using that module in your configuration files and do not have it enabled? After validating that the file exists try enabling the module with ```
sudo a2enmod ldap
```

---

### Post by Eviola on 2009-01-04
I already tried enabling/disabling mod_ldap and other modules... In fact, I disabled them all to see if that would help, as well as enabling them all as well.

Same problem :(

---

### Post by spiderbatdad on 2009-01-04
this article mentions some broken links: [http://beerpla.net/2008/07/29/how-to-fix-symbol-lookup-error-usrsbinhttpd2-prefork-undefined-symbol-apr_ldap_ssl_init-2/](http://beerpla.net/2008/07/29/how-to-fix-symbol-lookup-error-usrsbinhttpd2-prefork-undefined-symbol-apr_ldap_ssl_init-2/)
```
/usr/lib # ln -sf libaprutil-1.so.0.2.9 libaprutil-1.so.0
/usr/lib # ln -sf libapr-1.so.0.2.9 libapr-1.so.0

```

Also did you install apache2.2-common?

---

### Post by Eviola on 2009-01-04
I already read that article and tried relinking the files... No change :( And yes, apache2.2-common is installed.

---

### Post by RealPSL on 2009-01-04
Can you post your configuration files? It has to be something in the configuration referencing a directive from mod_ldap that is causing the problem. The hole in that hunch is that enabling the module would have fixed it.

---

### Post by Eviola on 2009-01-04
It's a straight out of the box Apache2 installation, so the configuration files are as they were...

apache2.conf
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

mods-enabled contains the following:
> alias.conf
alias.load
auth_basic.load
auth_digest.load
authn_alias.load
authn_anon.load
authn_dbd.load
authn_dbm.load
authn_default.load
authn_file.load
authnz_ldap.load
authz_default.load
authz_groupfile.load
authz_host.load
authz_owner.load
authz_user.load
autoindex.conf
autoindex.load
cgid.conf
cgid.load
dbd.load
deflate.conf
deflate.load
dir.conf
dir.load
env.load
include.load
ldap.load
rewrite.load
setenvif.conf
setenvif.load
ssl.conf
ssl.load
status.conf
status.load

.load files just contain the LoadModule lines for the appropriate module.

httpd.conf is an empty file (seems to use apache2.conf rather than httpd.conf which states that it's for user changes).

Let me know if you need any other files.

---

### Post by RealPSL on 2009-01-05
That looks fine can we get a look at the files in the sites-enabled folder.

---

### Post by Eviola on 2009-01-07
```
000-default -> ../sites-available/default
```

Contents of that file:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
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

Files inside conf.d:
charset:

```
# Read the documentation before enabling AddDefaultCharset.
# In general, it is only a good idea if you know that all your files
# have this encoding. It will override any encoding given in the files
# in meta http-equiv or xml encoding tags.

#AddDefaultCharset UTF-8
```

security:

```
#
# Disable access to the entire file system except for the directories that
# are explicitly allowed later.
#
# This currently breaks the configurations that come with some web application
# Debian packages. It will be made the default for the release after lenny.
#
#<Directory />
#	AllowOverride None
#	Order Deny,Allow
#	Deny from all
#</Directory>


# Changing the following options will not really affect the security of the
# server, but might make attacks slightly more difficult in some cases.

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
#ServerTokens Minimal
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory
# listings, mod_status and mod_info output etc., but not CGI generated
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
#ServerSignature Off
ServerSignature On

#
# Allow TRACE method
#
# Set to "extended" to also reflect the request body (only for testing and
# diagnostic purposes).
#
# Set to one of:  On | Off | extended
#
#TraceEnable Off
TraceEnable On
```

Again, all unchanged from original installation.

---

### Post by RealPSL on 2009-01-07
Wow you should not be getting that error especially if you have mod_ldap disabled. Does a configtest comeback clean? ```
sudo /usr/sbin/apache2ctl configtest
```

---

### Post by RealPSL on 2009-01-07
I hate to ask this but you seem to have an almost default configuration did you try just removing and installing it?

---

### Post by Eviola on 2009-01-08
> **RealPSL said:**
> Wow you should not be getting that error especially if you have mod_ldap disabled. Does a configtest comeback clean? ```
sudo /usr/sbin/apache2ctl configtest
```

Running any apache2ctl commands gives me that same undefined symbol error :(

> **RealPSL said:**
> I hate to ask this but you seem to have an almost default configuration did you try just removing and installing it?

Yep. Several times.

I think I might just give up on the package and compile it myself :\

---

### Post by Yoshikazu on 2011-10-20
I have just had the same problem with my Ubuntu 10.04LTS running on Dell Mininote.

I have 3 apaches on my Ubuntu. One is the original, and the others are the ones I built from the latest tarball. I tweak apache modules so I needed to have my own httpd. I have been using my own custom apache for a while, and then I tried the synpactic installed apache2. apr_ldap_ssl_init does not exist, it says.

There are two libs related to apr. /usr/lib/libapr-1.so and /usr/lib/libaprutil-1.so.
I ran nm on the two libs and found apr_ldap_ssl_init is in libaprutil-1.so. Actually I did have another apr libs under /usr/local. So I set a environment variable LD_LIBRARY_PATH:

# export LD_LIBRARY_PATH=/usr/lib

And ran "apache2ctl start" again, and it worked this time.

Cheers

---

### Post by maxxs on 2012-07-03
> **Yoshikazu said:**
> 
# export LD_LIBRARY_PATH=/usr/lib



Thanks!!! You save my life.

---

### Post by oldos2er on 2012-07-03
Old thread closed.

---

