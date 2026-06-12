---
title: "[SOLVED] how to set autostart commandos with sudo rights?"
date: 2007-10-31
forum: Desktop Environments
---

### Post by linuxd00 on 2007-10-31
hi,
to setup my trackpoint in ubuntu gutsy i need to set filerights and then change 2 files in every session(until my driver gets updated sometime. :()

Question:
how can i get this commandos in a kind of autostart? it is of course important that the sudo ones get executed first.


-------------------------
sudo chmod ogu+w /sys/devices/platform/i8042/serio1/speed
sudo chmod ogu+w /sys/devices/platform/i8042/serio1/sensitivity  
echo -n 100  > /sys/devices/platform/i8042/serio1/speed 
echo -n 230  > /sys/devices/platform/i8042/serio1/sensitivity
 -------------------------

i dont understand how to use the /etc/init.d files and the System->Preferences->sessions  doesnt seem to care about the order of the commands.

can somebody pls tell me how to do it or give me a pointer to look further?

 thanks in advance!

---

### Post by scrooge_74 on 2007-10-31
you could make a file with those commands (without the sudo) and leave it in your /home/user, then just type sudo sh filename for them to execute

---

### Post by linuxd00 on 2007-10-31
hi,
thats kinda what i do now...
but its quite odd to do it manually at every boot... i would really like to automate it.

---

### Post by sisco311 on 2007-10-31
just copy and paste the commands in your /etc/rc.local file
```
sudo gedit /etc/rc.local
```> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

chmod ogu+w /sys/devices/platform/i8042/serio1/speed &&  echo -n 100  > /sys/devices/platform/i8042/serio1/speed 
chmod ogu+w /sys/devices/platform/i8042/serio1/sensitivity   && echo -n 230  > /sys/devices/platform/i8042/serio1/sensitivity
exit 0

---

### Post by bswilson on 2007-10-31
Here's what you need to do.  The directory /etc/rc3.d contains scripts that execute whenever you start your system up in runlevel 3.  Most of the files in there are symbolic links because they are used in more than 1 runlevel.  But that's okay -- we can drop a script there that does what you want.

Open the text editor as root, by running this command:

```
gksudo gedt /etc/rc3.d/S30touchpad
```

The filename is one I just chose randomly; you can call it anything.  The capital S that the file starts with is just to tell you that it is a startup script and not a shutdown script.  In that file, paste this:

```
#!/bin/sh
#
# Update files at system startup
#
chmod ogu+w /sys/devices/platform/i8042/serio1/speed
chmod ogu+w /sys/devices/platform/i8042/serio1/sensitivity
echo -n 100 > /sys/devices/platform/i8042/serio1/speed
echo -n 230 > /sys/devices/platform/i8042/serio1/sensitivity
```

Save and exit, and you're all set.  The script that you called /etc/rc3.d/S30touchpad will run each time you boot up in runlevel 3 (the default, which I'm sure you're using).

---

### Post by linuxd00 on 2007-10-31
Thank you!
 the rc.local trick did it for me!

My ubuntu is now working the way i dreamt it!

---

### Post by scrooge_74 on 2007-10-31
Mark the thread as solved for the benefit of others

---

