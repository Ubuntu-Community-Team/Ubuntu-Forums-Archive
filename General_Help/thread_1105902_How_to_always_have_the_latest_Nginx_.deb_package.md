---
title: "How to always have the latest Nginx .deb package"
date: 2009-03-25
forum: General Help
---

### Post by docplastic on 2009-03-25
**The following procedure describes How To build a Nginx .deb package using the developer's latest sources.**

**# Tested on Ubuntu 10.04**

Published at: <[http://ubuntuforums.org/showthread.php?p=6953724](http://ubuntuforums.org/showthread.php?p=6953724)>


**Nginx** <[http://nginx.net/](http://nginx.net/)> is an open-source Web Server. It is a high-performance HTTP server that uses very low server resources, is reliable and integrates beautifully with Linux. 
Besides being a web server it can also be used as reverse proxy and IMAP/POP3 proxy server.

**## install needed debian tools**
sudo aptitude -R install build-essential devscripts fakeroot debhelper autotools-dev libpcre3-dev libssl-dev zlib1g-dev # libgcrypt11-dev

**## search bellow & replace by your own version number, maintainer name, maintainer email, domain**: 
	0.8.52
	dummy
	[email]dummy@example.com[/email]
        example.com
 
**## get latest STABLE nginx from the author's site:** <http://sysoev.ru/nginx/download.html>
cd $(mktemp -d) ; # create a temp dir and cd to it
wget [http://sysoev.ru/nginx/nginx-0.8.52.tar.gz](http://sysoev.ru/nginx/nginx-0.8.52.tar.gz)

**## get the sources from the debian/ubuntu repositories**
apt-get source nginx
sudo apt-get build-dep nginx
cd $(ls -d nginx*/)

**## update package info to new version**
(export DEBFULLNAME='dummy';export DEBEMAIL='dummy <dummy@example.com>';uupdate --upstream-version 0.8.52 ../nginx-0.8.52.tar.gz)
cd ../"$(dpkg-parsechangelog | sed -n 's/^Source: //p')-0.8.52"
sed -i '/^Maintainer/s/: .*/: dummy <dummy@example.com>/;/^Uploaders/s/: .*/: dummy <dummy@example.com>/;/XSBC-Original-Maintainer/d' debian/control; # customize maintainer data

**## 10.04 OPTIONAL: set ./configure & debian/rules, to our own specs**
#   see nginx compile-time options at: <http://wiki.nginx.org/NginxInstallOptions>
#   REMEMBER TO CAREFULLY (RE)CHECK ANY CONFIG CHANGES

sed -i '/nginx-upstream-fair.diff/d' debian/patches/series
rm debian/patches/nginx-upstream-fair.diff
grep -A 20 '\.\/configure' debian/rules
sed -i '/with-debug/,/nginx-upstream-fair/ c\
\t--with-http_ssl_module \\\
\t--without-http_limit_req_module \\\
\t--without-mail_pop3_module \\\
\t--without-mail_smtp_module \\\
\t--without-mail_imap_module \\\
\t--without-http_uwsgi_module \\\
\t--without-http_scgi_module \\\
\t--without-http-cache \\
' debian/rules

grep -A 20 '\.\/configure' debian/rules

**# OPTIONAL: anonymize nginx public fingerprint**
# do replace 0.0.00 and webserver by your own values
sed -i '/^#define nginx_version/s/[0-9]/0/g;/^#define NGINX_VERSION/s/".*"/"0.0.00"/;/define NGINX_VER\([ \t]*\)"/s/nginx/webserver/' src/core/nginx.h
sed -i '/SERVER_SOFTWARE/s/nginx/webserver/' debian/conf/fastcgi_params
sed -i '/our $VERSION/s/[0-9]/0/g' src/http/modules/perl/nginx.pm
sed -i '/>nginx</s/nginx/     /' src/http/ngx_http_special_response.c

# check if all went well
grep -i nginx_ver src/core/nginx.h
grep SERVER_SOFTWARE debian/conf/fastcgi_params
grep 'our $VERSION' src/http/modules/perl/nginx.pm
grep  -i nginx src/http/ngx_http_special_response.c

## OPTIONAL: to edit the change log use:  
#(export DEBFULLNAME='dummy';export DEBEMAIL='dummy <dummy@example.com>';dch -i);

**## build the new package**
(export DEBFULLNAME='dummy';export DEBEMAIL='dummy@example.com';debuild -i -us -uc);

**## install the newly built package**
cd ..
sudo dpkg -i nginx_0.8*deb && sudo aptitude hold nginx

**## OPTIONAL: customize /etc/nginx/nginx.conf**
grep 'tcp_\|worker_processes\|gzip\|keepalive_timeout\|tokens\|sendfile' /etc/nginx/nginx.conf
# set worker_processes = server CPU's
sudo sed -i '/^worker_processes/s/1;/'"$(grep -c processor /proc/cpuinfo)"';/' /etc/nginx/nginx.conf
# change gzip
(n=$'\n' ; sudo sed -i "/^\([ \t]*\)gzip\([ \t]*\)on;/ a\\${n}    gzip_min_length 640; \\${n}    gzip_types text/plain text/css application/x-javascript text/xml application/xml application/xml+rss text/javascript;" /etc/nginx/nginx.conf);
# set timeout to 10
sudo sed -i '/^\([ \t]*\)keepalive_timeout/s/keepalive_timeout.*/keepalive_timeout\t10;/' /etc/nginx/nginx.conf;
# set server_tokens off
(n=$'\n' ; sudo sed -i "/^\([ \t]*\)sendfile\([ \t]*\)on;/ a\\${n}    server_tokens   off;" /etc/nginx/nginx.conf);
# set tcp_nopush on
sudo sed -i '/#tcp_nopush/s/#//' /etc/nginx/nginx.conf;
grep 'tcp_\|worker_processes\|gzip\|keepalive_timeout\|tokens\|sendfile' /etc/nginx/nginx.conf

**## replace nginx trying to not disrupt the web services**
pgrep nginx && sudo kill -s USR2 $(cat /var/run/nginx.pid)
pgrep nginx >/dev/null && sudo kill -s QUIT $(cat /var/run/nginx.pid.oldbin)
sleep .5
pgrep nginx || sudo /etc/init.d/nginx start
sudo /usr/sbin/nginx -t && /etc/init.d/nginx status


## OPTIONAL: to turn debug mode on:
./configure --with-debug ...

nginx.conf:
events {
     debug_connection  your.ip.address;
}

--
**Resources**:
Rebuilding Debian packages <http://www.debian-administration.org/articles/20>
Nginx page <[http://nginx.net/](http://nginx.net/)>
Nginx Wiki <[http://wiki.nginx.org/Main](http://wiki.nginx.org/Main)>
Nginx Forum <[http://forum.nginx.org/](http://forum.nginx.org/)>

---

### Post by Belarios on 2009-06-25
What would be the command to change the name of the package?

I want to create a second .deb with debugging enabled, but it'd be nice to give the package a different name.

---

### Post by docplastic on 2009-06-26
> **Belarios said:**
> What would be the command to change the name of the package?

The command is: dch
It does a lot more than changing version numbering.

Check the specifics with:
man dch  ;# take a look at --create and --package

That's why this line is in the howto:
(export DEBFULLNAME='John Doe';export DEBEMAIL='jdoe@jdoe.0';dch -i); # update change log


J.

---

### Post by intel352 on 2009-09-23
This how-to worked great, except that I had to add debhelper to the list of packages to install (at the beginning of the list of commands that you have here). it was an unmet dependency found when trying to build nginx.

---

### Post by flibustier on 2010-02-12
Hello 

I need to add parameters for the ./configure

```
--with-debug --with-http_stub_status_module --with-http_flv_module --with-http_ssl_module --with-http_dav_module --with-http_gzip_static_module --with-mail --with-mail_ssl_module --with-ipv6 --add-module=../nginx_mod_h264_streaming-2.2.7 --with-http_realip_module --with-debug --sbin-path=/usr/local/sbin
```

How should this command look for me?
```
## OPTIONAL: customize ./configure in debian/rules, to our own specs
# see note bellow: "## (*1) debian/rules"
# EDIT AND CAREFULLY (RE)CHECK ANY CONFIG CHANGES
grep -A 8 '\.\/configure' debian/rules
sed -i '/http-fastcgi-temp-path/,/with-http_realip_module/ c\
\t--http-fastcgi-temp-path=/var/lib/nginx/fastcgi \\\
\t--with-http_ssl_module \\\
\t--without-http_limit_req_module \\\
\t--without-mail_pop3_module \\\
\t--without-mail_smtp_module \\\
\t--without-mail_imap_module \\\
\t--without-http-cache
' debian/rules
grep -A 12 '\.\/configure' debian/rules
```
Thank you

---

### Post by docplastic on 2010-02-13
@flibustier

Just add/replace lines started with \t-- by your own parameters.
Each \t-- parameter, in its own line.
Do use the updated sed -i '/with-debug/,/nginx-upstream-fair/...

M.

---

### Post by flibustier on 2010-02-18
> **docplastic said:**
> @flibustier

Just add/replace lines started with \t-- by your own parameters.
Each \t-- parameter, in its own line.
Do use the updated sed -i '/with-debug/,/nginx-upstream-fair/...

M.

Thank you, after your update everything went fine!

You need to add, that you have to run apt-get install dpatch

And I have such error:
> sudo sh -c "find /etc/nginx/ -name 'server.key' -print0 | xargs -0 chmod 0400 ; chown -R 0.0 /etc/nginx" ;# protect critical files
chmod: missing operand after `0400'
Try `chmod --help' for more information.

---

### Post by docplastic on 2010-02-19
> **flibustier said:**
> And I have such error:
sudo sh -c "find /etc/nginx/ -name 'server.key' -print0 | xargs -0 chmod 0400 ; chown -R 0.0 /etc/nginx" ;# protect critical files
chmod: missing operand after `0400'
Try `chmod --help' for more information.


It is the expected behavior if you do not have a ssl public key named "server.key" somewhere under /etc/nginx/.

M.

---

### Post by vrossign on 2010-04-10
that sounds great, I'm definitely interested in that!

2 questions: 

1/ How can I deal with additional modules Iwe want to build nginx with?
Configure option: --add-module=/path/to/module 

2/ Would it be possible to adapt this technique to build a php5.2.11 with php-fpm (php-fpm-0.6~5.2.11.tar.gz) from [https://launchpad.net/php-fpm/?](https://launchpad.net/php-fpm/?)

Thanks.

---

### Post by docplastic on 2010-04-11
> **vrossign said:**
> that sounds great, I'm definitely interested in that!

2 questions: 

1/ How can I deal with additional modules Iwe want to build nginx with?
Configure option: --add-module=/path/to/module 

2/ Would it be possible to adapt this technique to build a php5.2.11 with php-fpm (php-fpm-0.6~5.2.11.tar.gz) from [https://launchpad.net/php-fpm/?](https://launchpad.net/php-fpm/?)

Thanks.

1. After the line:
\t--with-http_ssl_module \\\
you may insert line(s), take care to replace  YOUR_MODULE_NAME_HERE with the module that you want to include (check the proper syntax at: <http://wiki.nginx.org/NginxInstallOptions>).
\t--with-YOUR_MODULE_NAME_HERE \\\

2. I have another post on how to setup php-cgi with nginx <[http://ubuntuforums.org/showthread.php?p=9106655](http://ubuntuforums.org/showthread.php?p=9106655)>.
It is very simple to setup, very fast and very reliable.
Regarding php-fpm, I would rather be safe (with the old faithful php-cgi), than sorry with the still toddler php-fpm.
I am sure that, in time, the php-fpm will become more mature and included in the main php package.

M.

---

### Post by vrossign on 2010-04-11
1/ Actually I'm talking about 3rd party addons ([http://wiki.nginx.org/Nginx3rdPartyModules](http://wiki.nginx.org/Nginx3rdPartyModules)). Docs says to enter the following line in the configure:

--add-module=/path/to/module/source

2/ Too bad. php-fpm seems a great alternative with many advantages. Anyway, I'll wait or keep my current compilation script.

Thanks

---

### Post by docplastic on 2010-04-12
> **vrossign said:**
> 1/ Actually I'm talking about 3rd party addons ([http://wiki.nginx.org/Nginx3rdPartyModules](http://wiki.nginx.org/Nginx3rdPartyModules)). Docs says to enter the following line in the configure:

--add-module=/path/to/module/source


Did you try to insert a line like the following?
\t--add-module=/path/to/module/source \\\

---

