---
title: "Java in Firefox"
date: 2006-07-28
forum: Desktop Environments
---

### Post by joehill on 2006-07-28
I've never been able to get Java to work in Firefox, so I was glad to see Java in its new .deb packages.  But after removing my old Java installation and installing the new packages from Synaptic, I still get the "Additional plugins are required" message in Firefox.  The curious thing is that Java now works fine on Galeon and Epiphany, just not Firefox.  I've checked and made sure there are no broken links from my failed attempts to follow previous how-tos, and I tried removing the sun-java5-plugin package entirely and reinstalling it again and nothing changed.  I looked at [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) but it seems to assume that all I need is the plugin package (I tried changing the jvm priority, etc.).  I'm glad it now works in Epiphany, but it would be nice if it worked in Firefox.  Thanks!

---

### Post by bardu on 2006-07-28
Try 
```
sudo update-alternatives --config firefox-javaplugin.so
```

and see what options are available. You should select a plugin from Sun.

Open Firefox and type 
 
    about:plugins  (I can't for the smily it should be : p without space)

and see whether the change took place.

---

### Post by joehill on 2006-07-28
Thanks Bardu.  update-alternatives gives me two Sun options, /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so and /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so, with the first being the default.  (These are not links to each other--I don't know what the difference is.  But the dates on both make me think both are from the new sun-java packages)  I tried both of them, and each time, about:plugins does not list a java plugin (it only lists the Shockwave Flash plugin). Hmmm.

---

### Post by bardu on 2006-07-28
Indeed, this is strange. Your default Java is okay, so I suppose if other applications working fine with Java your Firefox installation is the problem. Please look in /usr/lib/mozilla-firefox/plugins whether there is a symbolic link to libjavaplugin.so.

---

