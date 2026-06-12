---
title: "Compiz wont start"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by 4l13n666 on 2008-03-23
Hi.


I recently installed kiba-dock. Kiba dock runs fine along with everything else except CompizConfig.

When i run (or try to run) the compiz config by using the system tab icon, nothing happens. Nothing whatsoever. My desktop effects went away  to minimum but thats it. No other problems! i tried reinstalling compiz but it didnt change anything!

---

### Post by 4l13n666 on 2008-03-23
There seems to be a problem with my version of compiz config. (i think)

Well actually, when i hit the CompizConfigManager button nothing at all happens whatsoever.  No loading, no error, nothing.

Its as if it wasn't even there. BUT it has to be there because kiba dock is still working! I installed beryl but i have no idea of how it works and from my point of view it sucks.

I tried this command with the following error:

erik@erik-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
erik@erik-laptop:~$ 
erik@erik-laptop:~$

---

### Post by konungursvia on 2008-03-24
I'd remove beryl or compiz, and delete the icon that does nothing, reboot, and try executing compiz-config from the shell.

---

### Post by jimbo99 on 2008-03-24
Kiba-dock is a bit too gimmicky.  It isn't really an app that grandma would want to use.  Instead, you should try avant-window-navigator.

---

### Post by 4l13n666 on 2008-03-25
Yeah i\I do use AWN but I just wanted to know how to install kiba dock. I am going to remove kiba dock now.

I have removed both beryl and compiz completely and removed ever little trace of both of them and then i reinstalled CompizConfig but the problem still persists; but when I install beryl manager there is no problem and apparently I get a working version on CompizConfig with it. I am really confused i think i managed to install two CompizConfigs in different directories and one of them will not open.

---

