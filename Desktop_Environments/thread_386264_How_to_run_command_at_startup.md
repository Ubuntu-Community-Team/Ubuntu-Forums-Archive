---
title: "How to run command at startup"
date: 2007-03-16
forum: Desktop Environments
---

### Post by teet on 2007-03-16
Everytime I boot my computer I have to open up a terminal and type:
```
nohup ping -i 15 192.168.1.1 &
```
and
```
ivtv-tune -c 3
```

to have everything on my system work perfectly (the nohup ping command is to keep my BCM43XX from crashing and the ivtv-tune sets my tv tuner to the correct channel since I have to use an ir blaster to change my external digital tuner box).

Where should I stick these 2 commands to have them ran automatically at boot?

I do have a custom script sitting in /etc/init.d that is running at boot right now.  The contents of that file are:

```

#! /bin/sh
# /etc/init.d/homebrew: Loading the Homebrew IR receiver (IT'S ALIVE!).
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
lircd
ivtv-tune -c 3

```

I'm pretty sure I could stick the nohup ping command at the bottom of that script and it would work fine, but the ivtv-tune command doesn't work from the script (I think mythbackend is loading after this script is ran and is changing the channel to something other than 3 ... grrrrr!).

-teet

---

### Post by spin2cool on 2007-03-16
I'm not on my linux box at the momemnt, but I recall correctly, it's in the "Sessions" menu (under System>Adminstration)

---

### Post by pmark on 2007-03-17
There is also this file:

```
/etc/rc.local
```

That gets executed each time the OS boots. You need root priviledges to edit it. In order to edit it under Ubuntu (I do not know the graphical sudo command for Kubuntu and Xubuntu) press ALT+F2, then type:

```
gksudo gedit /etc/rc.local
```

After that, you can enter any commands you want.

---

### Post by teet on 2007-05-14
Wow, okay, so just a few months late, but whatever.

Thank you for your replies.  I ended up getting really busy and didn't have time to mess with stuff.  I ended up getting it to work.  I basically just created an incredibly simple script and added it to my sessions file.

```

cd /usr/local/bin
gksudo gedit name_of_file

```

This will open up a blank file named 'name_of_file'.  Then just insert the following lines:
```

#!/bin/bash
ivtv-tune -c 3

```
changing 'ivtv-tune -c 3' to whatever command you need to run.  Save the file and close gedit.  Then make the file executable by typing

```

sudo chmod +x name_of_file

```

Then go to System --> Preference --> Sessions.  Click on the 'New' button and in the command simply put 'name_of_file' (without the single quotes of course).  Done.

There is probably an easier way to do this (like editing the rc.local file) but this worked for me.

-teet



-teet

---

### Post by fakie_flip on 2007-06-08
> **pmark said:**
> There is also this file:

```
/etc/rc.local
```

That gets executed each time the OS boots. You need root priviledges to edit it. In order to edit it under Ubuntu (I do not know the graphical sudo command for Kubuntu and Xubuntu) press ALT+F2, then type:

```
gksudo gedit /etc/rc.local
```

After that, you can enter any commands you want.

a good way is to use the cron daemon. type the command.

```
crontab -e
```

if the command requires root privileges, then use this one instead.

```
sudo crontab -e
```

now you are using nano text editor. make a new line and add this.

```
@reboot command
```

push control w to save. push control x to exit. when you get asked questions about writing a new crontab, push y for yes. replace command with your command. when i did this. my command was getting ran too early, so i used the sleep command, and now everything works good.

```
sleep 10;command
```

---

