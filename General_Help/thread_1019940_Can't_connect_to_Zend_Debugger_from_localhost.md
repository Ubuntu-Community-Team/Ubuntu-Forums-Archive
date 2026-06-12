---
title: "Can't connect to Zend Debugger from localhost"
date: 2008-12-23
forum: General Help
---

### Post by briwood on 2008-12-23
I'm having trouble getting ZendDebugger.so to work.   Any suggestions?

Since I'm runing a Ubuntu Server 8.10 (a VM Ware image), I plan to connect to Zend Debugger from Eclipse running on my host OS.  As an initial test I believe I should be able to telnet to port 10000 to connect to the debugger (this works on a WAMP server that I have).   This doesn't work:

	```
$ telnet 127.0.0.1  10000
	Trying 127.0.0.1...
	telnet: Unable to connect to remote host: Connection refused
```

(Predictably I cannot connect to the debugger from my host OS either by telnet to 10000 nor from a correctly configured Eclipse SDK.) 

My Zend section in /etc/php5/apache2/php.ini:
	
	```
[Zend]
	zend_extension=/usr/lib/php5/20060613+lfs/ZendDebugger.so
	zend_debugger.allow_hosts=127.0.0.1
	;zend_debugger.allow_hosts=127.0.0.1/32, 192.168.73.0/24
	zend_debugger.expose_remotely=always
```

After restarting apache2 and loading a  phpinfo page I see all of the correct things (**see attached screen shots**)
	
No firewall is enabled. 

Should ```
netstat -ln -A inet
``` reveal something listening on port 10000?  It does not.  (On my WAMP server which has a working ZendDebugger, NETSTAT -A -N does show a listener on 10000.)

Also I am running rsync via xinetd.  Wondering if xinetd could be getting in the way, I stopped it, restarted apache, but still could not connect to port 10000.  

More info about the packages I have installed:

Ubuntu Server 8.10:

	```
$ dpkg --get-selections | grep php
	libapache2-mod-php5                             install
	php-config                                      install
	php-pear                                        install
	php5                                            install
	php5-cli                                        install
	php5-common                                     install
	php5-curl                                       install
	php5-gd                                         install
	php5-ldap                                       install
	php5-mysql                                      install
	
```
	```
$ dpkg --get-selections | grep apache
	apache2                                         install
	apache2-mpm-prefork                             install
	apache2-utils                                   install
	apache2.2-common                                install
	libapache2-mod-php5                             install
```

Thanks for reading.

---

### Post by briwood on 2008-12-23
Forgot to mention that I see this in /var/log/apache2/error.log

```

[Tue Dec 23 14:07:01 2008] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operations
Zend Debugger: Cannot read a valid value of zend_debugger.httpd_uid or zend.httpd_uid, will not perform dropping of privileges

```

Google doesn't turn up anything useful for that error.

---

### Post by briwood on 2009-01-06
I got XDebug working by following these instructions: [http://techmania.wordpress.com/2008/07/02/debugging-php-in-eclipse-using-xdebug/](http://techmania.wordpress.com/2008/07/02/debugging-php-in-eclipse-using-xdebug/)

I can now run a debug session from Eclipse PDT running on my host OS (Vista) and connect to XDebug on my ubuntu server running under VMWare.

In order to get XDebug working I needed to comment out the zend stuff in /etc/php5/apache2/php.ini

RE ZendDebugger.so: I was starting to think in terms of downgrading to Apache 2.2.8 to see if that resolves the error

> Cannot read a valid value of zend_debugger.httpd_uid or zend.httpd_uid...

---

### Post by stanimir on 2010-05-19
I have the same error in apache error log.
[Wed May 19 11:44:57 2010] [error] [client 127.0.1.1] [Zend Debugger] Host '192.168.159.128' is not allowed to open debug sessions - please configure zend_debugger.allow_hosts in your zend.ini file. Failed to connect to host '127.0.0.1'. 
[Zend Debugger] Cannot connect to hosts: 192.168.159.128,127.0.0.1

this error and stoping the Zend Debugger apear after system update:
in package manager safe-upgrade with excluding of apache and php. I think this is for some network package.. 
on port 10000 only listen tcp6.
tcp6       0      0 :::10000                :::*                    LISTEN

---

