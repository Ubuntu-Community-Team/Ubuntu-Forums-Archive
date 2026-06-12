---
title: "Java does not register in Firefox"
date: 2005-04-09
forum: Desktop Environments
---

### Post by lleonard on 2005-04-09
I've installed JRE using the instructions on ubuntuguide.org and "java -version" does indeed indicate that it is installed and working.  

Per the guide, I made symlinks in /usr/lib/mozilla/plugins/  and /usr/lib/mozilla-firefox/plugins/ but Java does not register in Firefox.

Following tips on this and other websites I also made a symlink in plugin directory in ~/.mozilla/ and tried deleting ~/.mozilla/firefox/pluginreg.dat.

Java still doesn't register. I'm sure the fix is blindingly obvious, but I'm missing it today.  

Can someone point me in the right direction?

---

### Post by joshmachine on 2005-04-10
lleonard.  Can you give more specifics?

when you say java doesn't register, what does that mean?  how are you testing this. 
When you type "about:plugins" in firefox java does not appear?

Although adding the symlink into the /usr/lib directories should make it available,  the symlink that you should put in your local directory should be in ~/.mozilla/plugins

Try starting firefox from a command prompt and see if you get any error messages.

Cheers

---

### Post by lleonard on 2005-04-10
Doh! 

I had the symlink in ~/.mozilla/firefox/plugins but not in ~/.mozilla/plugins .

Thanks!

---

