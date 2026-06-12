---
title: "Compiz settings not in effect after reboot/login"
date: 2012-05-09
forum: Desktop Environments
---

### Post by chilloutmo on 2012-05-09
Hello everyone,

I have the following problem: I have set the bottom left corner to window scale and the bottom right corner to show desktop. These effects do not work after login/boot. I have to open ccsm, remove the binding, click OK, reset the binding, click OK again and then it works. And then I have to do the same thing for the other corner. When I reboot the settings again won't work, although they are clearly activated and shown correctly in ccsm. 

Everything worked fine under 11.10 so I don't know what to do. My computer is Asus 1215n with a fresh install of 12.04 64bit and bumblebee. 

So far I tried putting the compiz --replace command in the startup applications, but while this worked once, it did not work afterwards anymore so I am back to square 1. 

Any help would be much appreciated. 

chilloutmo

---

### Post by Mahyar on 2012-05-16
I have the same problem with 'scale' in compiz after reboot.  I'm running 12.04 32-bit on an Aspire-5820TG.

Cheers

---

### Post by lynrock on 2012-05-16
The workaround mentioned here fixed it for me:
[http://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845]("http://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845")

---

### Post by Mahyar on 2012-05-16
Thanks, but it doesn't work.  Any other ideas?

---

### Post by ZOMGxuan on 2012-09-28
I think you just need to modify the workaround from the above link a little to get it to work for you.

You're currently having problems with the settings for Scale plugin not persisting across logins/reboots, which is probably because when the Unityshell plugin is loaded by Compiz, it rewrites the bindings for the Scale plugin, which is loaded earlier.

To fix this, try editing /apps/compiz-1/general/screen0/options/active_plugins key in gconf-editor and place 'scale' below 'unityshell'. This will make Compiz load the Scale plugin after the Unityshell plugin. Hopefully that will fix your problems! (It did for me when I was having problems with bindings in the Wall plugin disappearing after reboot.)

---

