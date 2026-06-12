---
title: "Menu/Taskbar not loading on startup and no ALT-F2"
date: 2008-05-17
forum: Desktop Environments
---

### Post by chsub on 2008-05-17
I've been using 8.04 since release as a recent convert to Ubuntu from Windows and so far have been very pleased with it. However I have come across my first problem which I can't solve!

I booted up today only to find my menubar and taskbars do not start (I had one at the top and a launcher bar at the bottom of the screen). I tried an ALT-F2 to get a box up so I could attempt to manually start them but the alt-f2 shortcut does not work either.

I managed to get firefox going by placing a 'Launcher' shortcut on the desktop and have searched to forums for a solution to the problem but can't find anything that helps. Does anyone know how I get get my menubars back and why the alt-f2 shortcut would stop working?

Many thanks in advance

---

### Post by prshah on 2008-05-17
> **chsub said:**
> Does anyone know how I get get my menubars back

Try restarting the gdm; switch to virtual terminal with Ctrl+Alt+F1, login, give the command ```
sudo /etc/init.d/gdm restart
```, then switch back with Ctrl-Alt-F7; has it come up?

Why did it disappear? No idea, but it happens to me as well from time-to-time (rare). Restarting gdm has fixed it in every case.

---

### Post by chsub on 2008-05-18
Thanks for the reply, I tried what you suggested and after restarting the gdm I get thrown back to the ubuntu login screen. After logging in the system just hangs with a beige screen. A forced restart leaves me in the same position of having no taskbar/menubar... any other ideas?

Thanks

---

### Post by chsub on 2008-05-20
I still can't get this working... is /etc/init.d/gdm the app the starts the taskbars?

---

### Post by presston on 2008-05-20
maybe

right key - add panel
right key on panel - add applet - ubuntu menu, task switch

---

### Post by AlbertTatlocksCap on 2008-05-20
Ok - I posted this possible solutin in another thread but heer it is again



Ok - I had the same problem after a fresh install install of 8.04 onto a scsi disk (apparently it seems to affect scsi and USB devices)

I used this to get around it for now

CTRL+ALT+F1 (or CTRL+ALT+F2 if that doesn't work)

Login in text mode

sudo rm /tmp/.X0-lock

startx

It should then start up OK

Then set Automatic login by:

System>Administration>Login Window>Security and then check Automatic Login

Ok - this means that you can only login with one username and it will be automatic so no login window for password - but it works and I suspect/hope there will be a fix in the near future

Hope it helps

---

### Post by Hamstermerc on 2008-05-20
I have a very similar problem. Once i login the ubuntu login music is all weird and stuttery and then Alt-F2 doesn't work, i have limited panel functionality and typing in most places doesn't work.  Any help please

---

### Post by VMC on 2008-05-20
I read where the command ' killall gnome-panel'  brought it back to life.

Also check under your home directory .gconf Make sure its there. Someone copied another users to that directory and it worked.

---

### Post by ulefr01 on 2008-06-08
> **chsub said:**
> I've been using 8.04 since release as a recent convert to Ubuntu from Windows and so far have been very pleased with it. However I have come across my first problem which I can't solve!

I booted up today only to find my menubar and taskbars do not start (I had one at the top and a launcher bar at the bottom of the screen). I tried an ALT-F2 to get a box up so I could attempt to manually start them but the alt-f2 shortcut does not work either.

I managed to get firefox going by placing a 'Launcher' shortcut on the desktop and have searched to forums for a solution to the problem but can't find anything that helps. Does anyone know how I get get my menubars back and why the alt-f2 shortcut would stop working?

Many thanks in advance

startup in Xterm safe mode on Login screen
then you come in an terminal window
Enter : 'gnome-panel &' 
you get your menu back

use 'System - Preferences - Sessions'
create a program 'gnome-panel'

---

### Post by Andyvan on 2008-06-08
FYI: This just happened to me, but I'm running Gutsy.  Running "gnome-panel &" brought up the rest of the desktop.

Events as I recall them:

[LIST=1]
[*]Unable to spawn any processes
[*]Rebooted to fix problem
[*]Logged in
[*]Saw a Gnome error message flash on the screen
[*]No menu/taskbar
[*]Control-Alt-Backspace, no Gnome error message this time, still bad
[*]Completely shutdown (removed power), no change
[/LIST]

I checked, and "ubuntu-desktop" still shows as installed.

The last set of changes I installed had some Evolution fixes  

It would be nice to track down the *cause* of this.

-- Andyvan

---

### Post by LIFE- on 2008-06-10
I've just had the problem of the taskbar vanishing. Hopefully this can help someone.

Changes made: install scsi controller, 1 scsi drive, uninstall of evolution (I *think* this is probably the cause - I uninstalled a few things I shouldn't have :S )

fstab also got messed up but I think that was to do with the addition of the new HDD.

Solution: I started synaptic from a terminal and installed "gnome-panel" and "gnome-applets" (and their dependencies - which includes some evolution thingy :D I'm new to linux so please excuse the lack of knowledge).

---

### Post by hayden92 on 2008-06-11
Thank you LIFE, 
I had that exact same problem. By re-installing those packages my desktop is running normally again. Although I did get an error message saying that one of the files was not working. I simply continued and it worked fine. I am new to Ubuntu and Linux as well, maybe I should listen to the warnings more! Also, it is great to see that others have had the exact same problems as myself, and it's not just me!

---

### Post by jm101dm on 2008-06-13
I too had uninstalled Evolution and installed Thunderbird and the updates were mainly for evolution.  I will give this a go later tonight.  My thread is at [http://ubuntuforums.org/showthread.php?p=5160008#post5160008](http://ubuntuforums.org/showthread.php?p=5160008#post5160008)
and I think updating the uninstalled Evolution created my problem.
Jeff

---

### Post by jm101dm on 2008-06-13
startup in Xterm safe mode on Login screen
then you come in an terminal window
Enter : 'gnome-panel &'
you get your menu back

The above suggestion worked for me. Thanks, Jeff

---

### Post by 1337hippo on 2008-06-26
> **AlbertTatlocksCap said:**
> Ok - I posted this possible solutin in another thread but heer it is again



Ok - I had the same problem after a fresh install install of 8.04 onto a scsi disk (apparently it seems to affect scsi and USB devices)

I used this to get around it for now

CTRL+ALT+F1 (or CTRL+ALT+F2 if that doesn't work)

Login in text mode

sudo rm /tmp/.X0-lock

startx

It should then start up OK

Then set Automatic login by:

System>Administration>Login Window>Security and then check Automatic Login

Ok - this means that you can only login with one username and it will be automatic so no login window for password - but it works and I suspect/hope there will be a fix in the near future

Hope it helps

this solved my problem! thanks!

i had the same exact problem as the OP- just staring at my wallpaper with no panels and alt-f2 wouldn't work..
 i wasn't as clever to make a launcher for firefox. i instead right clicked, made a new (empty) folder, and opened it in order to get into nautilus. then i went to /usr/bin/ and launched firefox manually. LOL i guess it accomplished the same thing.


the only thing i did today was install kubuntu-desktop (and the 500mb of dependencies) so i could try out KDE- when i logged out and switched my session to gnome, these problems presented themselves. so i just went into synaptic and removed everything KDE, hopefully i won't get anymore trouble.

---

### Post by Albert Que on 2009-05-07
Meaby you are using compiz.
Try to go to compiz setup dialog, check "gnome-compatibility" (if unchecked) and make sure than you have the correct option for "run_key".

That was my problem, easy... when you know what to do. ;)

---

