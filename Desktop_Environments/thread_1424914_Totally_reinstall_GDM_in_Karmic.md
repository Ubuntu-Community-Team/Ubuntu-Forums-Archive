---
title: "Totally reinstall GDM in Karmic"
date: 2010-03-08
forum: Desktop Environments
---

### Post by afrodeity on 2010-03-08
I have a bit of problem with GDM. It no longer is working. I have tried reinstalling it. Also tried downgrading to GDM-2.0 which merely introduces problems with xorg. I have KDM which is working fine. Only problem is my Gnome session is not being managed that well. Gnome panel applets for example, don't load properly.

I've tried apt-get purge gdm

Every time I reinstall GDM, the same problem. It freezes, so I can't enter my password for user. The change session button is frozen. Only thing which works is the button for handicapped people. Button for reboot, shutdown works but nothing happens. I can only restart in recovery mode, or remove GDM whereupon I get the KDM manager.

Worried that if I now remove KDM, I will have a totally useless computer. What solution does anybody recommend?

---

### Post by MooPi on 2010-03-08
I believe you will need to set up a custom xinitrc session so you can start your xsession from prompt ```
startx
```
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)
This link looks dated but may hold all the info you'll require.
Here is someone else's solution:
[http://ubuntuforums.org/showthread.php?t=1343764&highlight=custom+xinitrc](http://ubuntuforums.org/showthread.php?t=1343764&highlight=custom+xinitrc)

---

### Post by afrodeity on 2010-03-08
I can startx from command prompt, but what I'm looking for is how exactly to purge my system without totally destroying it. Some of the GDM config files must corrupted, they are merely reinstalling and using old config, and I can't seem to purge them using aptitude or apt-get, what do I remove and what do I keep?

---

### Post by MooPi on 2010-03-08
I'm guessing here so don't take my word as gospel truth. Your gnome config files need to be replaced I'm guessing. It sounds as if you've done a few modifications and they may be interfering somehow. I've read threads that describe which files to remove to reset the gnome-panel and am thinking this may be the ticket. After they are removed the default settings kick back in and reset the desktop. 

Okay I've found the post :[http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel](http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel)
Don't know if this will help or what steps you'll need to follow to get everything back to normal, but hope this helps

---

### Post by afrodeity on 2010-03-09
Thanks MOOPI, I'll keep that in mind. It will reset the panels INSIDE gnome. I want to reset the GDM configuration OUTSIDE. :)

(Meanwhile I managed to bork something quite crucial installing a new programme, so have to deal with that first]

---

### Post by afrodeity on 2010-03-09
I think it has something to do with the gdm2setup tool I installed. I uninstalled but still the problem

[https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

[https://bugs.launchpad.net/ubuntu/karmic/+source/gdm/+bug/395299?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/gdm/+bug/395299?comments=all)

---

### Post by afrodeity on 2010-03-10
The gdm2setup tool might be a clue as to what the problem is. 

Here is the solution:
in a terminal type:
```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type Boolean --set /apps/gdm/simple-greeter/disable_user_list True

```

which changes the behaviour of the GDM greeter. Doing this resolved the problem and I was able to login after a frustrating period in which nobody had any idea what to do.

I would therefore like to collect other GDM behaviour codes. Post them here if you have them. Thanks.

---

### Post by afrodeity on 2010-03-11
> **MooPi said:**
> I'm guessing here so don't take my word as gospel truth. Your gnome config files need to be replaced I'm guessing. It sounds as if you've done a few modifications and they may be interfering somehow. I've read threads that describe which files to remove to reset the gnome-panel and am thinking this may be the ticket. After they are removed the default settings kick back in and reset the desktop. 

Okay I've found the post :[http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel](http://ubuntuforums.org/showthread.php?t=1404506&highlight=reset+gnome-panel)
Don't know if this will help or what steps you'll need to follow to get everything back to normal, but hope this helps

This fixed my panel, thanks.

---

