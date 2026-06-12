---
title: "Wordpress issues"
date: 2009-06-17
forum: General Help
---

### Post by cloudstrifejr1 on 2009-06-17
Hello All,

I am fairly new to Linux. I have been using it for a few months and I am currently wanting to run Wordpress locally on 9.04. I am using the LAMP method to get Wordpress installed. I have been looking through the forums for post relating to the installation as well as other sites. One of which is this site:

[http://www.jonathanmoeller.com/screed/?p=235](http://www.jonathanmoeller.com/screed/?p=235)

Anyway, I have installed apache2, mysql-server-5.0, php5, php5-mysql and the Word press software here: [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)

I believe I have the /etc/apache2/apache2.conf setup correctly. I also believe that I have the wp-config.php configured correctly. Here is what it used to be:

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'root');

/** MySQL database password */
define('DB_PASSWORD', '');

/** MySQL hostname */
define('DB_HOST', 'localhost');

If I go to [http://localhost](http://localhost), I get a IT WORKS! page. If I go to [http://127.0.0.1/wordpress](http://127.0.0.1/wordpress), I get a prompt to download a phtml page. I don't know if there are anymore .conf filed I need to mess with or not. I tried restarting apache, but I get this error:

reaper@reaper-laptop:/var/www/wordpress$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2   
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I am lost as to what I could have done wrong. If anyone has any suggestions, please let me know. I would like to learn more about this in anyway possible.

Best Regards,

cloudstrifejr1

P.S. If anyone needs anymore info about anything that I have done, please let me know and I can post again. I just want to get this figured out...lol

---

### Post by Dysport on 2009-06-17
Could you post your apache2.conf file? 
Which version of PHP do you have installed?

---

### Post by cloudstrifejr1 on 2009-06-17
Here is my apache2.conf:

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
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
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
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
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
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

Include /etc/phpmyadmin/apache.conf

AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps


Currently I am using php5. If you need anything else, let me know ;)

---

### Post by Dysport on 2009-06-18
Try adding this line:
> DirectoryIndex index.htm index.html index.php

Or look for the DirectoryIndex-line in your vhost conf file (/etc/apache2/sites-enabled)

If that doesn't work, try moving the index.php entry to the first place, like this: DirectoryIndex index.php index.html index.htm

Any luck with that?

---

### Post by cloudstrifejr1 on 2009-06-18
So should it look like this?

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

Include /etc/phpmyadmin/apache.conf

[COLOR="Red"]DirectoryIndex index.htm index.html index.php [/COLOR]
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps

I looked at my /etc/apache2/sites-enabled folder, and the only file in there was a file called 000-default. The file had this info in it:

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

Not sure if this was the file you were referring to. I looked for the DirectoryIndex-line but could not find it. Does any of this info look out of place?

Thanks for responding to my question btw :)

---

### Post by cloudstrifejr1 on 2009-06-18
**Update**

I can now get to [http://127.0.0.1/wordpress/](http://127.0.0.1/wordpress/)

I had to clear the Firefox cache. Now when I go there, I get a "Error establishing a database connection" notice. I checked my /var/www/wordpress/wp-config.php file and this is what it currently has:

/** The name of the database for WordPress */

define('DB_NAME', 'XXXXXXXX');



/** MySQL database username */

define('DB_USER', 'XXXXXXXXX');



/** MySQL database password */

define('DB_PASSWORD', 'XXXXXXXX');



/** MySQL hostname */

define('DB_HOST', 'localhost');



/** Database Charset to use in creating database tables. */

define('DB_CHARSET', 'utf8');



/** The Database Collate type. Don't change this if in doubt. */

define('DB_COLLATE', '');


XXXXX- refers to my information. I believe I have followed the correct steps when setting up my DB. I used this website to get some help: [http://www.jonathanmoeller.com/screed/?p=235](http://www.jonathanmoeller.com/screed/?p=235)

Have any ideas?

---

### Post by Dysport on 2009-06-19
Try setting it up again. That's probably faster than dig for an error (maybe you've improperly set your mysql passwords?).

Also have a look at this: [https://help.ubuntu.com/community/WordPress]("https://help.ubuntu.com/community/WordPress")
and this: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by cloudstrifejr1 on 2009-06-19
Thanks for your help. I have been wanting to do a fresh install of 9.04 anyway, so this would make for a perfect time to do it. I will try the 2 links you provided and let you know how it turns out. :D

---

### Post by Dysport on 2009-06-19
I actually meant that you just set up WordPress again, not the whole system :lol:
But if you wanted to do a complete fresh install anyway then that's fine too 8-)

---

### Post by cloudstrifejr1 on 2009-06-20
So I have run into a little snag. I have completely re-installed 9.04 :p

I have installed LAMP ----> 

sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

All work good. Moving onto the wordpress page you told me about
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)
I have hit a snag. On the part where it ask you to do this:

sudo ln -s /usr/share/wordpress /var/www/wordpress 

sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost # use bash instead of sh on Gutsy

sudo /etc/init.d/apache2 restart

It then says to go to [http://localhost/wordpress](http://localhost/wordpress) and it should give you a option to click the wordpress link...etc.

But, all I get is a 404 not found page. Any ideas? I have followed the steps 1 by 1 perfectly. This is the only part I semi-understand. Thanks in advance :)

-cloudstrifejr1

---

### Post by Dysport on 2009-06-20
> **cloudstrifejr1 said:**
> 

sudo ln -s /usr/share/wordpress /var/www/wordpress 

sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost # use bash instead of sh on Gutsy

sudo /etc/init.d/apache2 restart



You only have to run these commmands if you haven't installed wordpress in your default web root directory. The "ln -s" command creates a symbolic link pointing to the directory where you installed wordpress. So the easiest way is to install wordpress directly into /var/www/wordpress - does that work?

---

### Post by cloudstrifejr1 on 2009-06-23
I have it installed in /var/www/wordpress. Still no dice. I think I might remove wordpress and install it again in /var/www/wordpress. Give it one last shot.

---

### Post by cloudstrifejr1 on 2009-06-23
Well good news! I managed to get it to work. I purged all of the LAMP installation files. Then I went through each one by installing it and testing them 1 by 1. FINALLY! After a few days, I managed to get to the wp-config.php page at [http://127.0.0.1/wordpress](http://127.0.0.1/wordpress).

Thanks for all of your help and advice!! :D

-Cloudstrifejr1

---

### Post by Dysport on 2009-06-23
Glad to hear that \\:D/
You might want to give us the link so we can see the result ;-)

---

### Post by cloudstrifejr1 on 2009-06-24
Sure thing. When I get home from work, I will take a screen shot or 2 and upload them, so you can see the awsome wonder that is known as wordpress :P

Thanks again!

---

### Post by cloudstrifejr1 on 2009-06-25
As promised :)

[[IMG]http://img257.imageshack.us/img257/7286/snapshot2p.th.jpg[/IMG]](http://img257.imageshack.us/my.php?image=snapshot2p.jpg)

[[IMG]http://img257.imageshack.us/img257/3149/snapshot1g.th.jpg[/IMG]](http://img257.imageshack.us/my.php?image=snapshot1g.jpg)

---

