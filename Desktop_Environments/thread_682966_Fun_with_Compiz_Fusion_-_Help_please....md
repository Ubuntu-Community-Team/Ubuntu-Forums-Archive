---
title: "Fun with Compiz Fusion - Help please..."
date: 2008-01-30
forum: Desktop Environments
---

### Post by jjoker0110 on 2008-01-30
Ok, Im not a total noob with linux and I can hold my own when it comes to fixing things but I am kind of stumped at this point. So I just got a new laptop and of course I put linux on it and Im putting some of the things I like on there (Thunderbird, wine, ect...) and I go and try to get compiz fusion to work and it does something, but its a nothing kind of something. So I try to get into compizconfig-settings-manager (ccsm) and nothing happens when I click on it so I open a terminal and type in ccsm and I get this out put. 
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```
I go and hit up google with part of the last line of this error and get about five pages, two of which are English and not much help at all. Ive tried reinstalling emerald, compizcomfig-settings-manager and one or two other things and Im out of ideas.
Any suggestions?:confused:

---

### Post by airbornemist6 on 2008-01-30
Hmmm, who makes your laptop?

---

### Post by jjoker0110 on 2008-01-30
I have a Toshiba Satellite P205.

---

### Post by erginemr on 2008-01-30
I have recently updated Compiz-Fusion from Gutsy Backports. Maybe updating your version can resolve your problem, if you have not done already. You need to enable security, updates, proposed, backports and what not from the "Updates" tab of Synaptic "Software Repositories" and press update.

---

### Post by airbornemist6 on 2008-01-30
You could also uninstall the ubuntu version and try using Git4CF Automator.Although, I can't garuntee that would actually fix anything at all.

---

### Post by jjoker0110 on 2008-01-30
Ok, I did some crazy uninstall and reinstall and got the ccsm to start. Now none of the effects are working :-/ Were getting somewhere at least:)

edit:
I found out why they aren't working, I had to click on the appearance and tell it to use my custom one but it tells me that "Desktop effects can not be enabled" So Ill see if I can figure it out. Any suggestions?

---

### Post by erginemr on 2008-01-31
But you can run the standard effects (same dialog), right? In other words, can you enable standard Compiz Fusion effects but cannot customize it, or does Compiz not work at all?

Besides, what is your graphics card brand, the output of "lspci | grep VGA" from the terminal and and the output of "cat /etc/X11/xorg.conf"?

---

### Post by airbornemist6 on 2008-01-31
Check your restricted drivers manager, if you don't have the restricted drivers for your video card enabled, enable them. If that doesn't work, well let's just hope it works.

---

