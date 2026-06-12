---
title: "Can't get Steam to work on 13.10"
date: 2013-10-21
forum: Gaming &amp; Leisure
---

### Post by tbrminsanity on 2013-10-21
Good day everyone,

I've upgraded to 13.10 and I can't get Steam to work.  When I launch steam I get the following messages:

[http://www.thomasboxall.com/img/errors/error1.png](http://www.thomasboxall.com/img/errors/error1.png)
[http://www.thomasboxall.com/img/errors/error2.png](http://www.thomasboxall.com/img/errors/error2.png)

  

When I try to install the missing packages I get this:
```
XXXXX@XXXXX:~$ sudo apt-get install libXrandr.so.2 libpangoft2-1.0.so.0 libpango-1.0.so.0 libfreetype.so.6 libfontconfig.so.1 libgobject-2.0.so.0 libglib-2.0.so.0 libgio-2.0.so.0 libgtk-x11-2.0.so.0 libgtk-x11-2.0.so.0 libgdk-x11-2.0.so.0 libpangocairo-1.0.so.0 libgdk_pixbuf-2.0.so.0 libcairo.so.2 libpango-1.0.so.0 libfreetype.so.6 libfontconfig.so.1 libgobject-2.0.so.0 libglib-2.0.so.0 libXi.so.6 libasound.so.2 libXrender.so.1 libdbus-1.so.3 libpng12.so.0 libgcrypt.so.11 libgssapi_krb5.so.2 libgnutls.so.26 libavahi-common.so.3 libavahi-client.so.3
[sudo] password for datblygwr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libXrandr.so.2
E: Couldn't find any package by regex 'libXrandr.so.2'
E: Unable to locate package libpangoft2-1.0.so.0
E: Couldn't find any package by regex 'libpangoft2-1.0.so.0'
E: Unable to locate package libpango-1.0.so.0
E: Couldn't find any package by regex 'libpango-1.0.so.0'
E: Unable to locate package libfreetype.so.6
E: Couldn't find any package by regex 'libfreetype.so.6'
E: Unable to locate package libfontconfig.so.1
E: Couldn't find any package by regex 'libfontconfig.so.1'
E: Unable to locate package libgobject-2.0.so.0
E: Couldn't find any package by regex 'libgobject-2.0.so.0'
E: Unable to locate package libglib-2.0.so.0
E: Couldn't find any package by regex 'libglib-2.0.so.0'
E: Unable to locate package libgio-2.0.so.0
E: Couldn't find any package by regex 'libgio-2.0.so.0'
E: Unable to locate package libgtk-x11-2.0.so.0
E: Couldn't find any package by regex 'libgtk-x11-2.0.so.0'
E: Unable to locate package libgtk-x11-2.0.so.0
E: Couldn't find any package by regex 'libgtk-x11-2.0.so.0'
E: Unable to locate package libgdk-x11-2.0.so.0
E: Couldn't find any package by regex 'libgdk-x11-2.0.so.0'
E: Unable to locate package libpangocairo-1.0.so.0
E: Couldn't find any package by regex 'libpangocairo-1.0.so.0'
E: Unable to locate package libgdk_pixbuf-2.0.so.0
E: Couldn't find any package by regex 'libgdk_pixbuf-2.0.so.0'
E: Unable to locate package libcairo.so.2
E: Couldn't find any package by regex 'libcairo.so.2'
E: Unable to locate package libpango-1.0.so.0
E: Couldn't find any package by regex 'libpango-1.0.so.0'
E: Unable to locate package libfreetype.so.6
E: Couldn't find any package by regex 'libfreetype.so.6'
E: Unable to locate package libfontconfig.so.1
E: Couldn't find any package by regex 'libfontconfig.so.1'
E: Unable to locate package libgobject-2.0.so.0
E: Couldn't find any package by regex 'libgobject-2.0.so.0'
E: Unable to locate package libglib-2.0.so.0
E: Couldn't find any package by regex 'libglib-2.0.so.0'
E: Unable to locate package libXi.so.6
E: Couldn't find any package by regex 'libXi.so.6'
E: Unable to locate package libasound.so.2
E: Couldn't find any package by regex 'libasound.so.2'
E: Unable to locate package libXrender.so.1
E: Couldn't find any package by regex 'libXrender.so.1'
E: Unable to locate package libdbus-1.so.3
E: Couldn't find any package by regex 'libdbus-1.so.3'
E: Unable to locate package libpng12.so.0
E: Couldn't find any package by regex 'libpng12.so.0'
E: Unable to locate package libgcrypt.so.11
E: Couldn't find any package by regex 'libgcrypt.so.11'
E: Unable to locate package libgssapi_krb5.so.2
E: Couldn't find any package by regex 'libgssapi_krb5.so.2'
E: Unable to locate package libgnutls.so.26
E: Couldn't find any package by regex 'libgnutls.so.26'
E: Unable to locate package libavahi-common.so.3
E: Couldn't find any package by regex 'libavahi-common.so.3'
E: Unable to locate package libavahi-client.so.3
E: Couldn't find any package by regex 'libavahi-client.so.3'
XXXXX@XXXXX:~$ 

```

How can I get Steam working under 13.10?

---

### Post by efflandt on 2013-10-21
I don't think you can use apt-get like that to install specific versions (read: man apt-get). Also if you are running 64-bit you may have to force package versions with :386 suffix. If I am not quite sure what I am doing or looking for, I use synaptic to search for and install packages instead of apt-get (I am not quite used to Software Center where things do not necessarily exactly match package names).

Note that Steam and Steam games are 32-bit, so if you are running 64-bit you might try installing "ia32-libs". And see if that automatically installs "ia32-libs-multiarch:386". I cannot say if that will resolve your missing libs in 13.10, but I installed ia32-libs in 12.04 for something else before I installed Steam beta back in January and have not had any trouble with missing libs for Steam or games that some people have had.

---

### Post by tbrminsanity on 2013-10-22
Sorry that didn't work.

---

### Post by MikeCyber on 2013-10-23
Installed yesterday and the steam installer does all this for you. See also my posting below of yesterday but I went back to 13.04 as for some nvidia problems.

---

### Post by tbrminsanity on 2013-10-23
Yeah Steam installed for me in 13.04, but I'm not going to downgrade just for Steam.  I'll send an email to Valve, maybe they just need to upgrade their drivers.  I find it shocking that they are still writting their games in 32bit.  I thought all new software would be in 64bit by now.

---

