---
title: "apache2"
date: 2009-04-07
forum: General Help
---

### Post by lsd33 on 2009-04-07
apache2 is not working, I installed it via sudo apt and it seems to be running on port 80... none of the files in /var/www seem to come up in the browser. when I visit localhost the browser hangs for a long time. Apache used to work. Im on ubuntu 7.10.

---

### Post by kryptikos on 2009-04-07
You're going to need to put a lot more information in your request to get people to assist you. Just saying "it used to work" or "it's hanging" doesn't help folks help you troubleshoot. 

It would be helpful to know what your configuration is - - list the contents of httpd.conf

Are there errors showing up in your apache2 error.log (/var/log/apache2/) file?

Are you sure it is listening on 80? (run: **sudo lsof -i TCP:80**)

Help others help you.....

---

### Post by lsd33 on 2009-04-07
cat error.log
[Sun Apr 05 03:31:00 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 configured -- resuming normal operations
[Sun Apr 05 15:29:37 2009] [notice] Graceful restart requested, doing restart
[Sun Apr 05 15:29:37 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 05 15:29:37 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.5 configured -- resuming normal operations
[Mon Apr 06 05:18:08 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Mon Apr 06 05:18:08 2009] [notice] caught SIGWINCH, shutting down gracefully
[Mon Apr 06 10:43:35 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.5 configured -- resuming normal operations
[Tue Apr 07 00:27:07 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Tue Apr 07 00:27:07 2009] [notice] caught SIGWINCH, shutting down gracefully
[Tue Apr 07 07:17:40 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.5 configured -- resuming normal operations
[Tue Apr 07 10:13:09 2009] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Tue Apr 07 10:13:09 2009] [notice] caught SIGWINCH, shutting down gracefully
[Tue Apr 07 10:13:16 2009] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Tue Apr 07 10:26:15 2009] [notice] caught SIGWINCH, shutting down gracefully
[Tue Apr 07 10:27:11 2009] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations

---

### Post by lsd33 on 2009-04-07
alex@alex-desktop:/var/log/apache2$ sudo lsof -i TCP:80 | grep apache2
apache2   10307     root    3u  IPv4 262599       TCP *:www (LISTEN)
apache2   10308 www-data    3u  IPv4 262599       TCP *:www (LISTEN)
apache2   10309 www-data    3u  IPv4 262599       TCP *:www (LISTEN)
apache2   10312 www-data    3u  IPv4 262599       TCP *:www (LISTEN)
apache2   10313 www-data    3u  IPv4 262599       TCP *:www (LISTEN)
apache2   10314 www-data    3u  IPv4 262599       TCP *:www (LISTEN)

---

### Post by lsd33 on 2009-04-07
httpd.conf is empty!! I reinstalled apache2 like so:
sudo apt-get remove --purge apache2
sudo apt-get install apache2
I am trying again.

I also tried 

sudo apt-get autoremove --purge apache2
sudo apt-get install apache2

---

### Post by lsd33 on 2009-04-07
I'll check for apache2.conf because I think apache2.conf is what apache2 uses...

---

### Post by kryptikos on 2009-04-07
Looking through what you posted...the webserver is listing, so that's good. I noticed some errors on startup. Yes, you are correct, ubuntu is using apache2.conf (each distro has their own layout for some reason...it is a minor annoyance IMHO)...what is the content of your apache2.conf?

---

### Post by Coreigh on 2009-04-07
On a more simple note, are you trying to access from the local computer or from a different computer? On the local LAN or a WAN or the internet at-large? Do you get a page not found, or server not responding, or some other error?

In addition to apache2.conf there is the /etc/apache2/sites-enabled/000-default file to define default and virtual sites, and various possibilities in the /etc/apache2/conf.d/ directory.

I am also using 7.10 and apache2, along with PHP and MySQL.

---

### Post by Iowan on 2009-04-07
> **lsd33 said:**
> 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
This one *might *be fixed by editing /etc/hosts file - add a line```
127.0.1.1 yourservername
```

---

### Post by lsd33 on 2009-04-07
looks like thats been done... but I'll try and set localhost as 127.0.1.1,
after attempting to reinstall 

contents of /etc/host:

127.0.0.1       localhost
127.0.1.1       alex-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I changed the /etc/hosts file
to 

127.0.1.1       localhost
127.0.0.1       alex-desktop

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

this did nothing for me, my webserver is up and running according to the output when i start apache2 from /etc/init.d ... but when I visit localhost in a browser it hangs for a while and then gives me a page load error.

---

### Post by lsd33 on 2009-04-07
> **Coreigh said:**
> On a more simple note, are you trying to access from the local computer or from a different computer? On the local LAN or a WAN or the internet at-large? Do you get a page not found, or server not responding, or some other error?

In addition to apache2.conf there is the /etc/apache2/sites-enabled/000-default file to define default and virtual sites, and various possibilities in the /etc/apache2/conf.d/ directory.

I am also using 7.10 and apache2, along with PHP and MySQL.

For starters I am simply trying to visit localhost from my own machine so that I may administer a mysql database via phpmyadmin, thats my only concern right now. This situation is wierd because all of this stuff USED TO WORK and stopped working. I will have a look at the virtual sites too..

taken from 000-default
DocumentRoot /var/www/

this is exactly as it should be...

---

### Post by lsd33 on 2009-04-07
apache2.conf




[HTML]#
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
#
PidFile /var/run/apache2.pid

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

User www-data
Group www-data

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
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



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
Include /etc/apache2/sites-enabled/[/HTML]




I wonder if any of this has to do with some firewall configuration??? I can't even ping myself at 127.0.1.1 127.0.0.1 or localhost!

---

### Post by kryptikos on 2009-04-07
You can't ping localhost or 127.0.0.1 indicates your main problem. The card isn't answering. Run**less /etc/network/interfaces** and let me know what it vomits out to you....

---

### Post by lsd33 on 2009-04-07
/etc/network/interfaces:


#auto lo
#iface lo inet loopback

---

### Post by kryptikos on 2009-04-07
There's your problem. You need to edit that file with whatever your favorite editor is and remove the '#' from both lines. The #'s are causing the kernel to ignore and not activate the loopback adapater. The rest cascades...no loopback, no 127.0.0.1, no answer by Apache. 

Once you have saved the file run: **sudo ifup lo**

You should be able to ping the localhost or 127.0.0.1 (your choice) and your browser should spit out your page and be good to go :)

---

### Post by lsd33 on 2009-04-07
You guys are the man.
kryptikos is the man.
I don't know how to administer beans otherwise I would.

Also, I dont know how the hell that happened... because I never edited that file.

---

### Post by kryptikos on 2009-04-07
Happy to help :) Have a good one!

---

### Post by Coreigh on 2009-04-07
What is defined as the DocumentRoot in "/etc/apache2/sites-enabled/default"? And is there a default doctype defined and is there an index page of the right kind in the directory defined as DocumentRoot?

my DocumentRoot is /var/www and in that directory I have a file named index.php, and I have index.php defined as an accepted default doctype.

I know I sound like I am talking to a simpleton but please do not take it that way. I only mean to be clear and cover the basics.

---

