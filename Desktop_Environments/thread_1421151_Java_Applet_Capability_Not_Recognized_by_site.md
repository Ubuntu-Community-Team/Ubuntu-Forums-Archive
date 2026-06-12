---
title: "Java Applet Capability Not Recognized by site?"
date: 2010-03-03
forum: Desktop Environments
---

### Post by celem on 2010-03-03
9.10 amd64. Java is fully enabled in my Firefox browser but one site that I would like to use doesn't seem to recognize it. Please see the attached screen shots. Any ideas?

---

### Post by yochaigal on 2010-03-08
I have the same problem. Ubuntu 9.10 i386.
Trying to play Dragondot.

[http://nmccoy.net/games/game06_dragondot/applet/index.html](http://nmccoy.net/games/game06_dragondot/applet/index.html)

Doesn't register. Why not?  I have both IcedTea and JRE6 installed.

---

### Post by yochaigal on 2010-03-08
I should mention that I have Namoroka installed.  And the plugin does not show up. Unfortunately I've cleansed my system of Firefox 3.5 --- so I can't test that the issue is really my browser version.

---

### Post by yochaigal on 2010-03-08
Fixed! I simply had to create a symlink from the java path to the plugins path.  I did:
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/libnpjp2.so


So in your case, do:
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/AMD64/libnpjp2.so ~/.mozilla/plugins/libnpjp2.so

Or wherever your plugin directory is.

---

### Post by celem on 2010-03-08
Thank you for the suggestion, but no joy. We don't seem to have the exact same issue. I put in the link that you suggested but the failure remained the same. Since the Java verification sites indicate correct operation, *libnpjp2.so* seems to being accessed within its primary directory.

I went to the Dragondot website and the game played without error (without the link to *libnpjp2.so* in place) so this indicates that our problems are different.

---

### Post by yochaigal on 2010-03-08
Perhaps there is some security layer imposed that the version of java you are using does not support (at least in linux/64-bit)?   Do you use any adblocking software.

---

### Post by celem on 2010-03-08
NO ad-blocking software. Pure Sun Java - java-6-sun-1.6.0.15. Since it passes multiple java testing sites without a problem I am having trouble figuring it out.

---

### Post by yochaigal on 2010-03-08
Right. It must relate to something to do with their particular applet.

---

### Post by Charles07 on 2011-02-16
Bah.

I had a semi-nice long response as to what I did but the internet ate it.  :-?

Basically, concerning streetsmart.com, I uninstalled all other JRE packages, restarted Ubuntu, installed the latest Sun JRE, made a symbolic link to the libjavaplugin_oji.so plugin like so (use the current version of course):

[http://www.java.com/en/download/help/5000012300.xml](http://www.java.com/en/download/help/5000012300.xml)

reopened firefox, and I was able to access the streetsmart.com tool.

It works with Chromium as well.

Hope this helps someone else.

---

