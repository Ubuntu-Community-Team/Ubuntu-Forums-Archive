---
title: "Auto start command on startup"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Stealth on 2005-04-14
I installed Lineak and got it working today, but everytime I start up Kubuntu I gotta type "lineakd &" in a console to start it up. How can I make like, a batch script like:
```
lineakd &
exit
```
or something, and have it start up automatically?

---

### Post by Knome_fan on 2005-04-14
You could simply place a script into ~/.kde/Autostart that does what you want.

---

### Post by Stealth on 2005-04-14
Ok, but what do I save it as? an sh? a bat? or something else?

---

### Post by Knome_fan on 2005-04-15
The extension you save it with doesn't matter.

Open your favorite editor and generate a file that looks something like this:

#!/bin/bash
lineakd &

save it in ~/.kde/Autostart under whatever name you like and make it executable:
chmod +x yourfile

That should be it.

---

### Post by Stealth on 2005-04-15
[QUOTE=Knome_fan]The extension you save it with doesn't matter.

Open your favorite editor and generate a file that looks something like this:

#!/bin/bash
lineakd &

save it in ~/.kde/Autostart under whatever name you like and make it executable:
chmod +x yourfile

That should be it.[/QUOTE]
 Awesome! It works, Thanks Knome_fan! :D

---

### Post by laissezfaire on 2005-04-18
I have a related problem:
Kaffeine told me that I have to run "hdparm -d1 /dev/dvd" to get smooth DVD playback. So I went ahead and created a script as explained above and placed in my home folder. However the script does nothing because it is not being executed as root. So my question is how do I make this script work (or another solution can be used) so that I donot have to type "hdparm -d1 /dev/dvd" every time I start my computer.

---

### Post by finster on 2005-04-18
[QUOTE=laissezfaire]I have a related problem:
Kaffeine told me that I have to run "hdparm -d1 /dev/dvd" to get smooth DVD playback. So I went ahead and created a script as explained above and placed in my home folder. However the script does nothing because it is not being executed as root. So my question is how do I make this script work (or another solution can be used) so that I donot have to type "hdparm -d1 /dev/dvd" every time I start my computer.[/QUOTE]

Will "sudo hdparm -d1 /dev/dvd" not do the trick?

---

### Post by ohman on 2005-04-18
[QUOTE=laissezfaire]I have a related problem:
Kaffeine told me that I have to run "hdparm -d1 /dev/dvd" to get smooth DVD playback. So I went ahead and created a script as explained above and placed in my home folder. However the script does nothing because it is not being executed as root. So my question is how do I make this script work (or another solution can be used) so that I donot have to type "hdparm -d1 /dev/dvd" every time I start my computer.[/QUOTE]
You can edit /etc/hdparm.conf for hdparm commands.  Make sure you use sudo, and at the bottom is the place to specify it for each individual drive.  Make sure to remove the line comment character (#) for it.

So, for you you would want to add 
```
command_line {
     hdparm -d1 /dev/dvd/
}
```

to the bottom of your /etc/hdparm.conf.

---

### Post by cwaldbieser on 2005-04-20
You could try putting a script to do it in /etc/init.d and sym-linking it in /etc/rc2.d.  Try Googling for runlevels (or maybe SysV runlevels).  Ubuntu normally boots into runlevel 2, which is different than some other distros.

---

### Post by oldforce on 2005-04-21
create a desktop shortcut and put it in ~/.kde/Autostart

---

### Post by saltydog on 2005-04-27
[QUOTE=cwaldbieser]You could try putting a script to do it in /etc/init.d and sym-linking it in /etc/rc2.d.  Try Googling for runlevels (or maybe SysV runlevels).  Ubuntu normally boots into runlevel 2, which is different than some other distros.[/QUOTE]

Do change configuration at startup, use Ubuntu Bootup Manager
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

