---
title: "iPod is messed up and won't mount"
date: 2005-12-20
forum: General Help
---

### Post by PrincessPeach on 2005-12-20
In a fit of deleting rage, I think I fdisked all of the partition tables in my iPod, including the one with the Apple OS.  I had iPod Linux installed previously, but deleted that too.  Now whenever I turn on or reboot my iPod, it goes to the apple logo, and then to the ipod Linux tux logo and that's about it.

I've read everything on the iPod Linux forum and tried I think everything mentioned here:
[http://ipodlinux.org/Troubleshooting#My_iPod_is_really_messed_up_how_can_I_fix_it.3F](http://ipodlinux.org/Troubleshooting#My_iPod_is_really_messed_up_how_can_I_fix_it.3F)

But still no luck.

When I check what's mounted on my computer, the iPod which usually is displayed as sda1 or something, is no where to be seen.  Nothing in /proc/scsi/scsi either.

Any advice is greatly appreciated.

---

### Post by jasmuz on 2005-12-21
Unfortunatly you "bricked" your iPOD, making it as useless as a paperweight.

Did you try restoring the firmware? If that dosent work...Find out how you can reinstall the iPOD original OS back,...wich will do the proper formatting.

Your iPOD wont mount because it isnt longer recognized by the system (open a terminal and type tail -f /var/log/messages and plug it in...you should get some message...please post)

---

### Post by ember on 2005-12-21
I messed up my own iPod shuffle once, too - the only thing that helped was using Windows and the iPod Tools from Apple. Maybe you'll try that.

---

### Post by PrincessPeach on 2005-12-21
I did the "tail -f /var/log/messages" command and got this:
```

 Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readwrite:/home/louise/.gconf" to a writable configuration source at position 2
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Dec 21 19:57:35 localhost gconfd (louise-9219): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Dec 21 19:57:43 localhost gconfd (louise-9219): Resolved address "xml:readwrite:/home/louise/.gconf" to a writable configuration source at position 0
Dec 21 20:03:24 localhost exiting on signal 15
Dec 21 20:03:25 localhost syslogd 1.4.1#17ubuntu3: restart.
```

---

### Post by Wolftastic on 2007-06-08
hey, i read your post in an effort to fix my problem, which is pretty much the saem as yours...my computer wouldn't even recognize/mount my ipod because i deleted something important (database maybe?). anyways, i went to the apple website to see what i could do about reformatting my ipod:
[http://www.apple.com/support/ipod/five_rs/](http://www.apple.com/support/ipod/five_rs/)

i followed this instructions on my friends computer with windows and it works fine now. only problem is it will erase everything (no big deal if there's nothing on it anyways!) and you have to have access to another computer with windows or macos. i didn't know you could format ipods with linux so i'm gonna check that out. 
hope something works for ya!

---

