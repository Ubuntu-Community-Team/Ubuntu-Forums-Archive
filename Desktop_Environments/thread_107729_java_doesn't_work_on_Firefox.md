---
title: "java doesn't work on Firefox"
date: 2005-12-23
forum: Desktop Environments
---

### Post by ernesto.kemp on 2005-12-23
Hi guys,
I'm fighting to make java works on Firefox for the last 2 days..:confused: 
(Ubuntu-5.10, Firefox 1.5)
I've install jre from synaptic, than using automatix, than manually.
Now I have on my PC jre1.5 from sun and jre1.4 from automatix installation.
Checked 1 billion times the simbolic links recommended at the
sun web page, and the browser option to enable java.
Nothing works at all.
Does anyone have a suggestion?
Thanks

---

### Post by Rackerz on 2005-12-23
Im guessing you'd do something similar as to what is listed here in the wiki.

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29#head-ef347c277a133b64af0600bd1bf24bc64e7038b8](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29#head-ef347c277a133b64af0600bd1bf24bc64e7038b8)

---

### Post by ernesto.kemp on 2005-12-23
Ok, i've followed the instructions to set simbolic links in /home/user/.mozilla/firefox (it was really missing..) and nothing
has changed.. java is still unoperating.
note: the path in my pc is
/home/user/.mozilla/firefox/plugins
plugins directory was created by myself as indicated in the link of your message.
Some information to help help me:

> ls -la
libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

and 
>ls -la /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so 
libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

??
I don't know what to do anymore..

---

### Post by rcurley on 2005-12-23
You need to put the symbolic link in /usr/lib/mozilla-firefox/plugins 

Rich

---

### Post by ZMaster on 2005-12-23
To create a symbolic link, the command is :

ln -s *Link target* *Link name*

like *rcurley* said, the firefox plugin path in Ubuntu is located in /usr/lib/mozilla-firefox/plugins. Assuming that java is installed in (on my system) /usr/java/jre1.5.0_04/, the command would be :

ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

---

### Post by ernesto.kemp on 2005-12-24
Hi ZMaster, I've tryed .. but java is still blocked.

My actions were:

I've canceled all previous simbolic links for
firefox <-> jre that I had, and 
set a new one following your instructions.
I'm using the Blackdown jre, installed by automatix, so
my link is set as: 

/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so

I've also set this jre as default one from the menu
system -> preferences -> jre-plugin-control-panel

hope to make it work , one day who knows..
thanks a lot

---

### Post by r0ll3r on 2005-12-29
Hi ernesto.kemp,
i was having a very similar problem, here is how i solved it.

[1] I downloaded sun java
[2] started firefox, but it was using the old 1.4 blackcomb java
[3] i removed the old java version through synaptic
[4] i started to test java version on this page: [http://javatester.org/version.html](http://javatester.org/version.html)
[5] then it started complaining about missing plugins, of course manual install is the only offered method
[6] i typed ```
about:plugins
``` into firefox to check out, is there any java plugin in use. there were no java plugin!
[7] as others already told, make a symlink to the plugin. it was not so obvious as i thought
[8] check "which firefox" in a shell. mine is "/usr/bin/firefox"
[9] check "ls -la /usr/bin/firefox". mine is "/opt/firefox" (because i use firefox 1.5 by manual install, found in another thread)
[10] check firefox directory/plugins/libjavaplugin_oji.so and make the correct symlink to (usually) /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
[11] if you don't want to hard-wire this plugin, wire to /etc/alternatives/firefox-javaplugin.so. of course this is also a symlink, check if it is correct (the reason to do this way is because step 12 and future java installs will usually modify this symlink)
[12] also recommended to run "sudo update-alternative --config java" and select the correct java offered

hope this helps a bit.

---

### Post by jarechu on 2005-12-29
Hey ernesto.kemp, I had the same problem, and solved with r0ll3r info.

I have made the symlink in the incorrect path. If you have installed firefox 1.5 with automatix surely your firefox path is /opt/firefox. There, in plugins directory I had a libjavaplugin_oji.so (but not a symlink to this file in java path), so I made a backup of this file (for security), removed it and then made the correct symlink to my libjavaplugin_oji.so (mine here /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so), and it works.

---

### Post by neels on 2006-01-11
for the firefox java plugin, try this one: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

