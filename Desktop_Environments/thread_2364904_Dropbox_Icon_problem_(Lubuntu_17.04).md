---
title: "Dropbox Icon problem (Lubuntu 17.04)"
date: 2017-06-29
forum: Desktop Environments
---

### Post by M_Mynaardt on 2017-06-29
Hi, All.

I installed Lubuntu 17.04 recently on a Netbook someone gave to me as a freebie.
It's working fine, with the exception of the Dropbox Icon.
I just get that funny does nothing icon instead of the Dropbox icon.
The daemon is working, though, because I do get notification about updates being done and such.

I found one work around this was in the terminal:
```
$ dropbox stop
$ dbus-launch dropbox start
```

However, it's mildly annoying to do that every time I boot up.

I tried to disable Dropbox in the autostart and have **dbus-launch dropbox start **manually inputed.
But the Dropbox keeps getting reselected every time I start up Lubuntu and I have to do that terminal business each time.

Does anyone know of a better way to get the Dropbox icon to show up properly each time?
I hope it's an easy fix.

Thanks in Advance!

---

### Post by M_Mynaardt on 2017-07-24
[SIZE=4]Addendum:[/SIZE]

Since I made my first post, I noticed that the Dropbox icon does not always misbehave.
Less than half the time it dose not show properly, but most of the time it does.

After a bit of experimenting, I made a bash file for getting the Dropbox icon to show properly.
I wait until the daemon message comes up telling me that the Dropbox files are synced.
Waiting for that daemon message may not be necessary.  It's just me erring on the side of caution.

Anyway, here is the bash script I put together to get the Dropbox icon showing up right and proper:
```
# !/bin/bash
# Use this just in case the dropbox panel icon doesn't work
echo turning off dropbox to restart with panel icon &&
dropbox stop && sleep 1s &&
echo restarting starting dropbox with the panel icon &&
sleep 1s && dbus-launch dropbox start
```

I discovered that there needs to be a pause between stopping Dropbox and relaunching it.
At least on my computer (Samsung N150 netbook).
Which is why I put the sleep statements in this script.

Anyway, I just thought I would post this here as my own solution to this Lubuntu Dropbox aesthetics issue.
Hope someone finds it helpful.

---

### Post by keyz on 2017-08-15
Hi there,

I had this problem ages ago and found the 
dbus-launch dropbox start
solution.

The problem, as you probarly know, is that
Menu > Preferences > Default applications for LxSession > Autostart > Manual Auto started application > Add
and inserting
dbus-launch dropbox start
does not reliably launch the Dropbox app code as it always should.
It often 'mis-fires' and instead loads the cryptic icon that does not identify dropbox on the panel.

The solution, I feel, is to use an autostart start-up script that I have full control of; 
/path_to/start_up.sh

I have attempted a number of solutions so far to get this start-up script working, and as yet it's not going.

As someone with a small modicum of bash scripting experience I would have though this a trival thing to do.
But not so, seemingly.

The answer, if you are on the same Lubuntu version as me, may be of some use to you also and increase system reliability.

The thread is here

[https://ubuntuforums.org/showthread.php?t=2368826](https://ubuntuforums.org/showthread.php?t=2368826)

---

### Post by mender27 on 2017-09-16
I tried the "dbus-launch dropbox start" workaround, but I feel like this bug should be reported. Is it evident whether it happens on other Ubuntu flavors?

---

### Post by oldos2er on 2017-09-16
It happens on Xubuntu too.

I believe it's been reported to Dropbox,  but I'm on my phone right now and can't easily verify that.

---

### Post by el-beltagy on 2018-05-23
I tried the following and it is working for me, My Lubutu is 18.04
Start> Accessories > File Manager PCMan FM
Right click and mark "Show Hidden"
go to location "/usr/share/applications"
select Tools > Open current folder in Terminal
terminal will pop up
Wright "Sudo gedit" and enter
Enter your root password and enter
gedit will pop up
from "Open" select other document and goto location "/usr/share/applications"
select dropbox and open
in dropbox file replace "Exec=dropbox stari -i" by "Exec=dbus-launch dropbox start"
Save
from file manager copy Dropbox file and paste in the following location "/home/[your user]/.config/autostart" over the existing file
Restart :)

---

### Post by speartip on 2018-05-24
> **mender27 said:**
> I tried the "dbus-launch dropbox start" workaround, but I feel like this bug should be reported. Is it evident whether it happens on other Ubuntu flavors?
It's no good reporting this bug to Ubuntu, as it's a problem from the Dropbox side. As far as I'm aware this is a problem on any system that doesn't use Nautilus as it's default file manager. 
My workaround on an xfce desktop can be found in the following post. In principle it should be the same in Lubuntu.
[https://forums.linuxmint.com/viewtopic.php?f=47&t=262522](https://forums.linuxmint.com/viewtopic.php?f=47&t=262522)

---

### Post by neatace on 2018-06-01
> **el-beltagy said:**
> I tried the following and it is working for me, My Lubutu is 18.04
Start> Accessories > File Manager PCMan FM
Right click and mark "Show Hidden"
go to location "/usr/share/applications"
select Tools > Open current folder in Terminal
terminal will pop up
Wright "Sudo gedit" and enter
Enter your root password and enter
gedit will pop up
from "Open" select other document and goto location "/usr/share/applications"
select dropbox and open
in dropbox file replace "Exec=dropbox stari -i" by "Exec=dbus-launch dropbox start"
Save
from file manager copy Dropbox file and paste in the following location "/home/[your user]/.config/autostart" over the existing file
Restart :)
Thanks el-beltagy, I had the same issue under ubuntu mate 18.04, and tried the workaround mentioned previouly (it works). But I need a automatically solution which can help me out, and this really does.

---

### Post by oldos2er on 2018-06-03
Old thread closed.

---

