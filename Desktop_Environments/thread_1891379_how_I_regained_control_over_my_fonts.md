---
title: "how I regained control over my fonts"
date: 2011-12-05
forum: Desktop Environments
---

### Post by tazzarias on 2011-12-05
My setup:
ubuntu 1104
desktop GUI: Gnome 2.x


Issue: I was frustrated that my changes to my local ~/.fonts.conf file were _apparently_ not being honored by Firefox and other programs.


So ... I set FC_DEBUG=1024 in a shell, and then monitored which config files were loaded and in which sequence by starting FF from a shell window.  The debugging revealed the order in which fontconfig files were being loaded by FF, and hence applied fontconfig rules work such that the LAST config files loaded are the RULES which are in effect (contrary to much information  out on the web).  Sequence determined as highest number is last loaded.
   
  The debugging revealed that the following sequence of conf files in /etc/fonts/conf.d where in effect by default:
<... a bunch of other files loaded  ...>
  50-user.conf
  51-local.conf
< ... followed by a bunch of other files loaded ...>


  As a result, the 51-local.conf rules were overriding the rules I specified in ~/.fonts.conf, due to the sequence #s.  51-local.conf made reference to other local configuration files, which were turning on antialiasing (smoothing), autohinting, etc, which yielded blurry fonts in FF.  And _FF obeyed those rules, so it wasn&#8217;t a FF rendering issue after all_.
   
  Fix: mv 50-user.conf to 99z-user.conf to GUARANTEE that MY ~/.fonts.conf rules are to be in effect.  Then, tweak local ~/.fonts.conf to my heart's content, no FF restart was even needed, just reload the pages in FF to see the changes once the updated ~/.fonts.conf file is automatically reloaded after a few seconds.

  

Hope that helps some other folks out there.


Thx, Tazzarias

---

