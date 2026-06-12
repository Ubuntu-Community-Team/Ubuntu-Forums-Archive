---
title: "Netscape security model is no longer supported."
date: 2005-11-18
forum: Desktop Environments
---

### Post by jnie on 2005-11-18
I have installed Java jre1.5-sun under */usr/lib*, and created the symbolic link under */usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so* to point at */usr/lib/jre1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so* 
I've set the Java console to show, when starting an applet. When I try to start a specific applet, it gives me the error message :```

Netscape security model is no longer supported.
Please migrate to the Java 2 security model instead.
```

I'm not sure if this has to do with a missing certificate from the website or not?

Other than that I have no idea of what this means, Google shows me no signs!

Jan

---

### Post by jnie on 2005-11-22
[QUOTE=jnie]I have installed Java jre1.5-sun under */usr/lib*, and ...

I'm not sure if this has to do with a missing certificate from the website or not?
[/QUOTE]

It's not the certificate.

I tried the Blackdown jre, and let the install script setup the plugin for Firefox. Had no luck with this either, now it just stalled when trying to run my banking applet.

Jan

---

### Post by jnie on 2005-12-01
[QUOTE=jnie]It's not the certificate.

I tried the Blackdown jre, and let the install script setup the plugin for Firefox. Had no luck with this either, now it just stalled when trying to run my banking applet.

Jan[/QUOTE]

I found the solution to my particular problem.
The error I posted in the first, had nothing to do with the actual problem.
My exact problem was, my banking applet needing a .key file, the file i copied from a windoze partition was named .KEY uppercase letters. I renamed the file and the applet works. Even though I have an occasional error, as the one I described, it does not affect the functionality of the applet itself.

Jan

Author of :
[intotheLinuxWorld]("http://intothelinuxworld.blogspot.com")

---

