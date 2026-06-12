---
title: "Gnome broken, Crash, no panel nothing"
date: 2006-11-21
forum: Desktop Environments
---

### Post by shane2peru on 2006-11-21
Help, I broke my favorite desktop!!!  I'm glad I have KDE installed so I can boot into it!  Here is what happened.  Well, first I'm using Dapper 6.06 - the Christian edition.  What I did was followed this [thread]("http://www.ubuntuforums.org/showthread.php?t=301119&highlight=human+blue") and when I tried to install a new theme, Gnome started to crash.  Very few things worked, and my panel disappeared.  I had to hit Ctrl + Alt + Backspace to get out of Gnome.  I tried to log back in, and there was no panel, no nothing.  Only Kopete started up, and I was looking at a blue screen.  The panel kept trying to load, it would pop up, then disappear.  Right clicking & Left clicking did nothing!  Alt & F2 - nothing, I could get nothing to work except the Crtl + Alt + Backspace.  That was it.  Please help, I don't want to be stuck in KDE, and I really don't want to re-install again.  ](*,)  I have used Gnome for a while, and never broke it this bad, it resembles a Windows Crash, but at least Windows recovers when you reboot!  (Most of the time)

Shane

**EDIT:**  Oh, by the way, I tried logging into Gnome -Safe or Failproof or something, and it didn't work, not a very fail proof plan.

---

### Post by tater_3001 on 2006-11-21
same thing happened to me a while back. do you get the gconf messages like i did? idk mb its different but mine started working again after a week just out of nowhere haha mb yours will too... Turner

---

### Post by shane2peru on 2006-11-21
> **tater_3001 said:**
> same thing happened to me a while back. do you get the gconf messages like i did? idk mb its different but mine started working again after a week just out of nowhere haha mb yours will too... Turner

Tater,

I think I read your post.  No, that was a big difference, I didn't get any errors.  Nothing just a serious crash.  I can't wait a week.  That is too annoying.  There must be a reason and a fix.  I guess using KDE will have to do, however I really like the clean smooth functionality of Gnome, not to mention the support!  Hopefully they (support) will show up here soon.

Shane

---

### Post by shane2peru on 2006-11-22
Ok, I fixed it with the help of #ubuntu on IRC.  I had to create a new user and transfer all my things over to the new user account.  We did fix the problem, but discoverd another.  I had upgraded to Edgy, then downgraded back to Dapper, and left my /home directory.  That has been giving me headaches ever since.  New user fixed it for me, and then I will delete the old user and re-make it and transfer everything back the new-old user.  - Just in case someone comes across this and needs help.

Shane

---

### Post by misGnomer on 2006-12-02
Is there a howto somewhere for fixing Gnome configuration and crashing woes?

I recently did clean install of Edgy but used my old /home and Edgy (or Gnome) might have created some personality confusion with system UIDs and GUIDs since I had to create a new user (I used my existing username and pw) during install. I wonder if "sudo chown userid:userid /home/userid" would do any harm.

I also used "switch user" from the Quit menu and switched between two (different ID) Gnome sessions and the first shutdown after that seemed to leave me in limbo, or half-exited, with some unknown config resolve issues until eventually "shutdown -r now" kicked in and rebooted.

While now Gnome itself starts up (I had trouble getting even to GDM until I replaced the UUID entries in /etc/fstab into straight partition entries), the panel died once and even the new plain one keels over if I attempt accessing its Properties. Some Gnome apps like system-monitor or rhythmbox die before opening with no console legend, just a core dump, while others launch successfully and others have lethal quirks.

/var/log/messages has number of entries referring to GConf errors:

```
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): starting (version 2.16.0), pid 4722 user 'MyUserID'
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readwrite:/home/MyUserID/.gconf" to a writable configuration source at position 1
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec  1 12:04:00 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec  1 12:04:04 ubuntu gconfd (MyUserID-4722): Resolved address "xml:readwrite:/home/MyUserID/.gconf" to a writable configuration source at position 0
Dec  1 12:14:01 ubuntu gconfd (root-5119): starting (version 2.16.0), pid 5119 user 'root'
Dec  1 12:14:01 ubuntu gconfd (root-5119): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec  1 12:14:01 ubuntu gconfd (root-5119): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Dec  1 12:14:01 ubuntu gconfd (root-5119): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec  1 12:14:01 ubuntu gconfd (root-5119): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec  1 12:14:01 ubuntu gconfd (root-5119): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
```

Also, simple actions like opening "replace" function in Gedit can kill the app.

Any tips towards potential fixes or a howto on regenerating a healthy Gnome around existing user ID will earn you loads of good karma.  :^)

misGnomer

---

### Post by erdalronahi on 2006-12-04
I have similar issues. Are these gconfd messages really error messages? I have plenty of them. Also, lots of crashing gnome-panels.

---

