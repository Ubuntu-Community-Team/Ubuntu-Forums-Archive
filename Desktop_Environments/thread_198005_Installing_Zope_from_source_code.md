---
title: "Installing Zope from source code"
date: 2006-06-16
forum: Desktop Environments
---

### Post by meitham on 2006-06-16
Hi,

I am trying to install Zope from source code. I am using Ubuntu 6.06 LTS - the Dapper Drake. I have python2.4 installed and I am trying to instal zope2.8.7. I used the command

[FONT="Courier New"]./configure --with-python=/usr/bin/python2.4[/FONT]

and it worked well. But, when I later used [FONT="Courier New"]make[/FONT]. I have got this error

[FONT="Courier New"]building 'AccessControl.cAccessControl' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -IExtensionClass -IAcquisition -I/usr/include/python2.4 -c AccessControl/cAccessControl.c -o /home/meitham/Zope-2.8.7-final/build-base/python-2.4/build-temp/AccessControl/cAccessControl.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
make: *** [build] Error 1[/FONT]

It looks like if I miss [FONT="Courier New"]cAccessControl.o[/FONT] !!!! where else I can find it. I downloaded the whole source code from zope.org.

Does anyone have any suggestion?

Thank you

---

### Post by vigleik on 2006-06-16
Is it very important to have version 2.8.7? Version 2.8.6 is in the repos. (It also looks like 2.8 uses python2.3 while 2.9 uses python2.4, but it's possible that I'm wrong and this changed from 2.8.6 to 2.8.7 and this is why it's important for you to use version 2.8.7.)

Vigleik

---

### Post by meitham on 2006-06-17
[QUOTE=vigleik]Is it very important to have version 2.8.7? Version 2.8.6 is in the repos. (It also looks like 2.8 uses python2.3 while 2.9 uses python2.4, but it's possible that I'm wrong and this changed from 2.8.6 to 2.8.7 and this is why it's important for you to use version 2.8.7.)

Vigleik[/QUOTE]
It is important, but I will install Plone after. and the available version of Plone does not work on Zope 3 which what I have as a package. I am tryin to install everything from source code to avoid versions compatibility.

---

### Post by Nyati on 2006-06-18
Hi

[COLOR="DarkOrange"]Quote:[/COLOR] [[COLOR="YellowGreen"]I am trying to install Zope from source code. I am using Ubuntu 6.06 LTS - the Dapper Drake. I have python2.4 installed and I am trying to instal zope2.8.7. I used the command

./configure --with-python=/usr/bin/python2.4

and it worked well. But, when I later used make. I have got this error

building 'AccessControl.cAccessControl' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -IExtensionClass -IAcquisition -I/usr/include/python2.4 -c AccessControl/cAccessControl.c -o /home/meitham/Zope-2.8.7-final/build-base/python-2.4/build-temp/AccessControl/cAccessControl.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
make: *** [build] Error 1

It looks like if I miss cAccessControl.o !!!! where else I can find it. I downloaded the whole source code from zope.org.

Does anyone have any suggestion?[/COLOR]]

I was getting a similar error, however I'm also surprised that you're trying to use Python2.4. From what I've read, for Zope and Plone to work you need to use Zope2.8.7 with Python2.3.5.

I've been struggling to get my Zope Instance created but succeeded this morning. 

I think you should rather install Python2.3.5 as I think Python2.4 is still under a security audit.

Check back soon for a HowTo I'm compiling for Zope and Plone under DapperDrake.

---

### Post by Nyati on 2006-06-18
Hi

I've hit a brickwall that seems to be unsolved at present with the Dapper Drake release.

After successfully creating a ZopeInstance, I can't $.../.../.../runzope.

Even if I browse to [http://localhost:9673](http://localhost:9673) or port 8080 I'm unable to connect.

It also appears that this problem existed with zope2.7. The problem here is that the Debian package is set up to start all instance in /var/init.d/zope2.7 with the 'start' command, hence: /var/init.d/zope2.7 start

Unfortunately, even after installing all packages correctly, I searched through /var/init.d/ and could only find 'zope3'. This obviously doesn't work.

---

