---
title: "[xfce] cannot change resolution"
date: 2013-02-06
forum: Desktop Environments
---

### Post by caesar753 on 2013-02-06
Hello everybody,

i have a strange issue: i was trying to change screen resolution in xfce/xubuntu desktop and i cannot do it, googling on the internet i found out that i had to disable gnome services, because they take over the desktop and its options; so i disabled nautilus, dropbox, gnome-keyring, gnome-scrennesaver. 
For a while i could change screen resolution and have dual monitor but at a certain moment i couldn't do anything of these things.
Gnome services are all turned off but, if i go to xfce4-settings-manager i cannot change resolution and dualize monitors...
Any tips? Thanks! ):P

---

### Post by The Cog on 2013-02-06
I use arandr in xubuntu and have not had any problems with that, so it might be worth a try.

---

### Post by caesar753 on 2013-02-06
Thanks for the answer! Yes, i have read about arandr, and it works really fine, but i'd like to know why xfce4-settings-manager sometimes works, sometimes not ... 
Do you have any idea where i can read logs or anything similar about it?
Thanks

---

### Post by The Cog on 2013-02-06
> **caesar753 said:**
> Do you have any idea where i can read logs or anything similar about it?
ThanksSorry, I don't. The best thing I can think of is to launch the settings manager from the command line, and see if it prints any error messages as it fails.

---

### Post by caesar753 on 2013-02-06
thanks for your tip but nothing :(

---

### Post by caesar753 on 2013-02-07
Finally i fixed the issue:  i had to delete many item from ~/.config/autostart/ like blueman, blutooth, evolution-alarmnotify, jockery, notification daemon, gnome-authentication-agent, update-notifier, logged out and in and now xfce4-display-settings functions like a charm!!

thanks for your support!!

---

### Post by The Cog on 2013-02-07
That's weird. I can't see anything there that I would expect to affect your ability to change resolution. Anyway, glad to see you got it working.

---

### Post by caesar753 on 2013-02-09
Yes, you were right, this is a weird situation, but finally i managed to fix it!
So today i tried again to change monitor and resolution and again xfce4-display-settings wasn't working :-( well, again i deleted all the items in .config/autostart/ but, this time, nothing happened ...
So i googled again and found out that it was a known issue ([https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/331751]("https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/331751")), well, i followed this tip:

*"Update: I played with file permissions of this file (~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, added write permissions for all) and now at least I can change refresh rate. I still cannot change resolution, but it may be another bug as I can see display-config is actually trying to do something."*

And also i set display.xml permissions rwx for everybody, and now it works, really!!!

---

### Post by caesar753 on 2013-02-23
Ok, perhaps it was not solved before, when i wrote the previous message, but now it is really solved:
for some strange reason xfce4-display-settings worked for a couple of time, but then it began again with its problems :-( i lose my hopes and went on using arandr ... 
but i noticed that in the output of the command 
```
 ps aux| grep gnome
```

there was still an entry of gnome services: it was gnome-keyring daemon ...
Well: today, finally, i have managed to stop this service by editing the file /etc/pam.d/lightdm, i had to comment out this line

```

auth    optional        pam_gnome_keyring.so

```

and now it seems than no gnome service is running and i can change the resolution from xfce4-display-manager!!

---

