---
title: "[SOLVED] panels not responding  ubuntu 8.10"
date: 2008-11-15
forum: Desktop Environments
---

### Post by madmax1735 on 2008-11-15
hey i am using ubuntu 8.10 on samsung x05 notebook.
the panels just stop responding and the notification applet or any other applet on the right side of the panel never show up. after boot.
also the menus dont work....... but i can use everything through terminal (has to be started through shortcut keys) 

i cant shutdown gdm.... gives as error that process is already running........

earlier the gnome used to start , used to hang at login prompt if a usb device was attached (even optical mouse)

help!

---

### Post by mssever on 2008-11-15
> **madmax1735 said:**
> hey i am using ubuntu 8.10 on samsung x05 notebook.
the panels just stop responding and the notification applet or any other applet on the right side of the panel never show up. after boot.
also the menus dont work....... but i can use everything through terminal (has to be started through shortcut keys) 

i cant shutdown gdm.... gives as error that process is already running........

earlier the gnome used to start , used to hang at login prompt if a usb device was attached (even optical mouse)

help!

Try this:

At the GDM login screen, hit F10 and choose "Session." From the dialog that comes up, choose "Failsafe terminal." Then, log in.

You should get a screen with a terminal and nothing more. The objective here is to start all the pieces of your session from a terminal so we can see any error messages that occur. Type the following commands one at a time, and make a note of any errors that are printed. Then post those errors here. CAUTION: If you close the terminal window, you'll be logged out.
```
metacity &
gnome-panel &
gnome-settings-daemon &
```If those commands work without error, log out and start over, this time giving the command ```
gnome-session &
```

---

### Post by madmax1735 on 2008-11-15
okey ............. how do i copy text of the terminal......... the usual right click copy is not working

cltr+C throws me out of gnome with the single terminal open.... the one that comes at the starting of the fail safe session 

i can restart gnome by gnome-session again...

---

### Post by madmax1735 on 2008-11-15
thnx a ton
its fixed now

after runnin all the commands i got error about few applets which were the cause of the problem , mostly g2ipmsg applet it coundnt be configure or something like that............. i was not able to copy the out of the commands.....

after runnin all the commands just normally boot into ubuntu.... it worked for me............... even though i logged into a system which had no sound (it was muted.... dont know how it managed to do that all by itself though)

---

### Post by timjohn7 on 2008-11-16
I have a similar problem, but worse.  My desktop has stopped functioning altogether.  I have my background pocture and nothing else... no Panels, no alt F2, no left or right click.  I can switch to other similarly non-functioning desktops, but nothing else.
Failsafe Gnome gives me same results, as does creating a new user.
Any advice?
mssever?

---

### Post by mssever on 2008-11-16
> **timjohn7 said:**
> I have a similar problem, but worse.  My desktop has stopped functioning altogether.  I have my background pocture and nothing else... no Panels, no alt F2, no left or right click.  I can switch to other similarly non-functioning desktops, but nothing else.
Failsafe Gnome gives me same results, as does creating a new user.
Any advice?
mssever?

Follow the troubleshooting steps in post two above, then post back with the results.

---

### Post by timjohn7 on 2008-11-16
Thanks mssever... I couldn't copy the results from the failsafe terminal (How does one? Shft Control C didn't work) but here they are:
metacity &
5398
gnome-panel &
5406
Gdk Warning **:/build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

This appears to be the problem... what now?
I haven't rebooted but wanted to post this before starting gnome-session

---

### Post by mssever on 2008-11-16
> **timjohn7 said:**
> Thanks mssever... I couldn't copy the results from the failsafe terminal (How does one? Shft Control C didn't work) but here they are:
metacity &
5398
gnome-panel &
5406
Gdk Warning **:/build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

This appears to be the problem... what now?
I haven't rebooted but wanted to post this before starting gnome-session

You can redirect the output to a file. For example: ```
metacity > metacity.log 2>&1 &
gnome-panel > gnome-panel.log 2>&1 &
```The > symbol says to redirect standard output (stdout) to the named file (such as metacity.log). NOTE THAT THIS WILL OVERWRITE THE FILE IF IT EXISTS WITHOUT WARNING. Use >> instead if you prefer to append to the file, instead of overwriting it. The 2>&1 means to redirect standard error (stderr) to the same place as stdout. Without redirection, stdout and stderr both go to the terminal.

I've never seen a GDK warning like the one you posted. Do you really have a /build directory? If so, why? It looks like something's screwy on your system. Did you perhaps install GDK by some means other than a .deb package? You might have hosed your system.

Another worthwhile test would be to see if GDK is itself hosed. Before starting gnome-panel, see if you can start some other simple GTK program from the terminal--such as gnome-calculator. It is telling that you can't even use another user account.

---

### Post by timjohn7 on 2008-11-17
Thanks for the lesson. As a relative noob I appreciate this kind of explanation rather than cut&paste.
Original install was from Alt CD and all has been fine. This problem started immediately after the 27-8 kernel update.
The panels were restored after the gnome-panel command despite the warning & I can confirm that changing user makes no difference.
Should I move/delete the /build directory?
Reinstall?
As always, thanks for the time & help.

---

### Post by mssever on 2008-11-17
> **timjohn7 said:**
> Thanks for the lesson. As a relative noob I appreciate this kind of explanation rather than cut&paste.
Original install was from Alt CD and all has been fine. This problem started immediately after the 27-8 kernel update.
The panels were restored after the gnome-panel command despite the warning & I can confirm that changing user makes no difference.
Should I move/delete the /build directory?
Reinstall?
As always, thanks for the time & help.

Ideally, you should figure out how the /build directory got there and undo whatever you did to put it there. Perhaps you compiled something from source?

Otherwise, you can try to delete /build and see what happens. Worst case: you hose your system and have to reinstall. The alternative, is reinstalling, so it's worth a shot.

But if you can figure out how /build got there in the first place, you'll learn much more than you would by reinstalling. Here's a wild stab in the dark. Maybe the kernel update scripts found the libs in /build and decided to use them instead of the standard ones (if that's the case, you might have to reinstall the kernel packages in addition to removing /build). Again, this isjust a wild guess. The bigger question is: what did you do that resulted in /build, and what else did it do to your system. The standard tools shouldn't result in such a directory. It's also possible that /build isn't the problem at all, even though it's presence is unexpected.

---

### Post by timjohn7 on 2008-11-17
All I did was run update manager which installed the new kernel. I'm years away from compiling anything from source!
I'll try deleting /build &get back to you.
How would I reinstall the kernel if I need to?
BTW, where is your chair in the world?

---

### Post by timjohn7 on 2008-11-17
Ok... there is no /build directory (or its hidden deeper than normal!)
Where to now?  Is there a better way to search in Terminal than find -L?

---

### Post by mssever on 2008-11-17
> **timjohn7 said:**
> How would I reinstall the kernel if I need to?In Synaptic, search for packages with names that contain linux. You should find the kernel packages there. There are several of them. The name includes the version number, so I can't just tell you the name.
> BTW, where is your chair in the world?
Currently in Texas, USA, but soon to be in Korea.
> **timjohn7 said:**
> Ok... there is no /build directory (or its hidden deeper than normal!)
Where to now?  Is there a better way to search in Terminal than find -L?
Have you tried [FONT="Courier New"]ls /[/FONT] ? If there's no /build, then something thinks that /build exists when it really doesn't. In that case, reinstalling GTK might help. To do that, open up synaptic and search for packages whose names begin with libgtk. Reinstall all such packages that are currently installed. (You don't need to worry about packages that currently aren't installed, but do make sure that ubuntu-desktop is installed--assuming you're running Ubuntu, not Xubuntu or something.)

By the way. I don't think a kernel update can cause the problems you're experiencing. I know you don't think you did anything else, but there must have been something--though I don't have the foggiest idea what it might be, and you probably don't have enough experience yet with Linux to have any ideas.

---

### Post by timjohn7 on 2008-11-17
The problem seems to be deteriorating... I'm now getting kernel panic messages on trying to reboot and segmentation fault messages when I try to boot in recovery mode or trying sudo apt-get dist-upgrade.
I decided to reinstall but get segmentation faults when trying to install from LiveCd.
I am/was running Ubuntu but with XFCE desktop after I got the problem (that was the only way I could do anything until I read this post).
I agree that something other than the kernel update caused the problem, but you are quite right, I have no idea what it was or could have been.
I wondered where you were due to the timezone difference and what must have been some weird hour for you yesterday?
I'm ex-Navy, so if you're going to Korea because of a military connection, good luck & enjoy it!
I'm replying from my laptop as I try to fix my desktop machine, so I'll get back to you once there is some life there.

---

### Post by mssever on 2008-11-17
> **timjohn7 said:**
> The problem seems to be deteriorating... I'm now getting kernel panic messages on trying to reboot and segmentation fault messages when I try to boot in recovery mode or trying sudo apt-get dist-upgrade.
I decided to reinstall but get segmentation faults when trying to install from LiveCd.Ugh. That doesn't sound good. If you're getting segfaults both in recovery mode and in the LiveCD, that sounds like some hardware's kicked the bucket. My first thought would be your RAM. Try running memtest86 (available from the GRUB prompt and also the live CD) for a while--maybe a day) and see if it finds any problems with your RAM.
> I'm ex-Navy, so if you're going to Korea because of a military connection, good luck & enjoy it!
Actually, I'm going to teach English. I always enjoy visiting other parts of the world. I've been to Zimbabwe several years ago, but never made it to South Africa.

---

### Post by timjohn7 on 2008-11-17
I'm getting some progress with LiveCD... it's found an error but continued and is now running live.  Can you suggest some checks I can run from LiveCD on my HDD?

Things are going well here in South Africa, and the exchange rate is really good for you at the moment, so either on the way to Korea or on the way back, why not stop over for a great holiday?

---

### Post by mssever on 2008-11-17
> **timjohn7 said:**
> I'm getting some progress with LiveCD... it's found an error but continued and is now running live.  Can you suggest some checks I can run from LiveCD on my HDD?Not really. You can try reinstalling and see if that helps. Otherwise, the RAM check can't be run from within Linux, and I don't know too much about hardware.

> Things are going well here in South Africa, and the exchange rate is really good for you at the moment, so either on the way to Korea or on the way back, why not stop over for a great holiday?
```
~:$ rand
KPh657v1
~:$ rand
lajjFkUN
~:$ rand
b4WTUn5C
~:$ rand
uUxkDMM9
~:$ 
```I haven't gotten any rand so far to pay for the trip; just letters, no numbers. Perhaps there's a better way... :)

---

### Post by hamena314 on 2008-11-18
I had a similar problem but solved it otherwise. Maybe this helps another person?
[http://ubuntuforums.org/showthread.php?t=986321](http://ubuntuforums.org/showthread.php?t=986321)

HAVE PHUN!

---

