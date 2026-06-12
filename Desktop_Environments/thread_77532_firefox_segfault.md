---
title: "firefox segfault"
date: 2005-10-17
forum: Desktop Environments
---

### Post by sharmaravi on 2005-10-17
Hi,

there seems to be something really wrong with firefox in breezy. It crashes all the time. It is not possible for me to surf the web continously for 15 minutes. when i start it from console, after the crash, all it says is segmentation fault. Is anybody else having this problem? any clue what can be done to fix this. 

I have following plugins installed.
flashplayer
mplayerplugin-3.11
Realplayer gold (nphelix.so)
Java(TM) Plug-in 1.5.0_05-b05
Adobe reader 7.0

I had totem plugin, but i removed it. 

-ravi

---

### Post by sharmaravi on 2005-10-17
*bump*

---

### Post by Stolen on 2005-10-17
same issue here.
I'm thinking about uninstalling all the plugins/browser and re-installing them. :/  
I don't have the adobe 7.0 plugin.

I've got:
mplayerplug-in 3.05
flashplayer
Java(TM) Plug-in 1.5.0_04-b05
Helix DNA Plugin


I'm noticing that it's been crashing a lot on my when I hit the back button (But also when I click on links.  After restart the browser, the link works fine)

---

### Post by sharmaravi on 2005-10-17
Thanks for sharing ur experience. It would be nice if can post the results after uninstalling/installing firefox. I was going to do the same thing but wanted to ask in the forums first in the hope of finding a definite solution.

Thanks.

---

### Post by ions on 2005-10-17
FireFox has never been stable for me.  It got slightly better after I removed the extension Tabbrowser Preferences but it still crashes.  The only error that comes up is 'segmentation fault'.  Doesn't seem to matter what I'm doing it will crash.  It's even crashed while idling with no sites in any of the tabs.

---

### Post by sharmaravi on 2005-10-20
guys i really need some help on this. My firefox is not usable for doing anything serious. HELP !!!

---

### Post by ions on 2005-10-24
Some 'theorists' I have I have spoken to blame the Flash plugin.  Flash does suck hugely so I wouldn't be surprised if it were responsible.  One way to check is to remove ALL your extensions and try your browser for a while before installing another one.

---

### Post by macmils on 2005-10-27
I've been having the same problem and found it was the Flash Plugin.

The Flash plugin was having a problem with the Composite extention I had enabled in /etc/X11/xorg.conf for all the fancy compostite fades.

Soon as I had disabled the Composite Extention Flash plugin worked again. So far, no more crashes

---

### Post by sharmaravi on 2005-10-27
Thanks guys for the reply. Few days back, I moved to firefox 1.5 beta and made it my default browser. It has not crashed even once and it is using all the same extensions and plugins. My xorg.conf has composite extension but I switch on shadow/fading rarely.

---

