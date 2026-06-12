---
title: "Create a symlink that requires root permissions to create on startup:"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Flyn on 2005-12-17
In /dev I only have a dspW device, not dsp as is expected by the majority of programs. If I create a symlink to it named dsp, everything works fine, but I need to do it each time the computer is rebooted, and I can't find a way to create this symlink on startup since it requires root permissions to create. Any tips?

---

### Post by cwaldbieser on 2005-12-17
[QUOTE=Flyn]In /dev I only have a dspW device, not dsp as is expected by the majority of programs. If I create a symlink to it named dsp, everything works fine, but I need to do it each time the computer is rebooted, and I can't find a way to create this symlink on startup since it requires root permissions to create. Any tips?[/QUOTE]
If you symlink a script to create the /dev/dsp symlink in one of the SysV init folders (e.g. /etc/rc2.d), it will run as root at boot time, and you can create it then.  Make sure you have it run *after* the device is actually created.

---

### Post by schdefan on 2005-12-17
You have to write a script that creates the symlink```

#!/bin/bash
ln -sf /dev/dsp /dev/yourlink
```

save your_script.bash and  make it executable
```
#chmod +x your_script.bash
```

move that script to /etc/init.d/
```
#mv your_script.bash /etc/init.d
```
and create a link to start it a boot time with

```
#update-rc.d your_script.bash defaults
```
Take a look at /etc/rc5.d
Now your symbolic link will be created at boot time

schdefan

---

### Post by schdefan on 2005-12-17
cwaldbieser: 
As far as i know the /dev entries are created with udev which is loaded in /etc/rcS.d which is loaded before the SysV scripts. So no problem to put it in /etc/rc2.d

schdefan

---

### Post by Flyn on 2005-12-17
Thanks a million guys!

I've been collecting quite a bit of data on Steam and Wine in the last couple of days, and I haven't found a complete howto for Ubuntu concerning the two. I wonder if there is any interest in me making one? Just a thought, in any case, thanks again.

---

### Post by ben22 on 2008-07-07
Hi,

I want the contents of folder A to be displayed in folder B with the help of a symbolic link.

So what I entered into terminal 

```
ln -s /home/user/A /home/user/B
```

It is working half - instead of having the contents of folder A inside of folder be, folder B now contains the folder A.

What command do I need to have contents for folder A to be linked into folder B?

thx,
Ben

---

