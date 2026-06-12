---
title: "PHP 5.1.1 w/ Payflow Pro extensions"
date: 2006-01-10
forum: General Help
---

### Post by skinnysweaty on 2006-01-10
Hi everyone,

I'm trying to configure PHP to use the Verisign Payflow Pro extensions ([http://us3.php.net/manual/en/ref.pfpro.php)](http://us3.php.net/manual/en/ref.pfpro.php)).  I've followed the directions at the php.net site for this, I have the Linux SDK (I actually have ALL the SDKs, and am opting for the regular Linux SDK rather than the RedHat9 SDK).  Here is my configure command (I've inserted newlines to make it readable):

```
'./configure' '--prefix=/usr/local' '--exec-prefix=/usr/local' 
'--includedir=/usr/local/include' '--libdir=/usr/local/lib' '--libexecdir=/usr/libexec' '--cache-file=../config.cache' 
'--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' 
'--enable-force-cgi-redirect' '--enable-pic' '--disable-rpath' 
'--enable-inline-optimization' '--with-dom=/usr' '--with-exec-dir=/usr/bin' 
'--with-gd' '--enable-gd-native-ttf' '--with-ttf' '--with-gettext' 
'--with-iconv' '--with-png' '--with-regex=system' '--with-xml' 
'--with-expat-dir=/usr' '--with-zlib' '--with-layout=GNU' '--enable-bcmath' 
'--enable-exif' '--enable-ftp' '--enable-magic-quotes' '--enable-safe-mode' 
'--enable-sockets' '--enable-discard-path' '--enable-track-vars' 
'--enable-trans-sid' '--enable-wddx' '--enable-mbstring' 
'--enable-mbstr-enc-trans' '--enable-mbregex' '--without-oci8' 
'--with-kerberos=/usr/kerberos' '--with-mysql=shared,/usr/local/mysql' 
'--enable-memory-limit' '--enable-bcmath' '--enable-shmop' 
'--enable-calendar' '--enable-dbx' '--enable-dio' '--enable-mcal' 
'--with-apxs2=/usr/local/apache2/bin/apxs' 
'--with-pfpro=shared,/opt/verisign/payflowpro/linux' 
```

Yes, I've copied pfpro.h to /usr/local/include and the library file libpfpro.so to /usr/local/lib.  Yes, the SDK really is at /opt/verisign/payflowpro/linux.

I've done this successfully with FreeBSD, so I know that it's not that complicated to set up.  Does anyone here have any advice or experience with setting up PHP for use with the Payflow Pro extensions on Ubuntu?  While I'm not a Unix newbie at all, I've only been working with Ubuntu for a short period of time...any gotchas that I may have missed? :confused: 

edit: The reason why I'm having a problem is when I try to kick off a simple pfpro_init(); function I get the message "Fatal error: Call to undefined function pfpro_init() in /var/www/test/nasmd/phpinfo.php on line 11"  That message basically says that the function/extension doesn't exist and isn't useable.


Thanks for your time.

---

