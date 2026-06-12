---
title: "Help! My unity is missing, cant see Launcher at all...just bg image."
date: 2015-07-29
forum: Desktop Environments
---

### Post by Aisiv on 2015-07-29
So, okay, I've been using Ubuntu 12.04 and this just came out yesterday when the launcher disappeared. I cant right click on screen 'cause nothing happens, I can open TTY with ctrl+alt F1, F2 and so on...I've been able to run a terminal with

[COLOR=#006400]DISPLAY=:0 gnome-terminal
[/COLOR]
And switch to it with Ctrl+alt+F7. I do this in case something goes wrong with TTY. I also can run nautilus with

[COLOR=#008000]sudo nautilus
[/COLOR]
I can access to my desktop and files but everything looks bad and basic, I can't access to media e.g. a usb wich I want to backup my files in. Here are the things that I already tried:
[COLOR=#008000]
DISPLAY=:0 ccsm [/COLOR]

Which seems.to be okay, first time I went there, Unity was unchecked and I checked it and clicked okay to the additional dialogs that checked another options also like OpenGL...After this, nothing happened. I rebooted like 6 times and same. Weird thing.is that when I reset to defaults the Unity option unchecks itself.

[COLOR=#008000]unity --reset 
WARNING: no DISPLAY variable set, setting it to :0
 ERROR: the reset option is now deprecated[/COLOR]

Then I run the display =0 and it just goes.with the last error.

Other tries:
Updating nvidia Drivers
 Removing nvidia Drivers
 Installing nvidia Drivers
 ReInstalling nvidia drivers
 Same with Compiz, Unity, Unity Desktop, fglrx, and Xorg. 
Reseting lightdm 
Changing to GDM
 Unity Tweak Tool 
Reseting compiz with dfcon-tool
 Installing Xubuntu to have the kind of back up desktop manager...but same ..nothing
Updating kernel headers (which I.cannot do.because of dependences and it says it.is not installable) 
I need to say this that I think is where the problem is... whenever I open Unity from the terminal and/or TTY, it crashes; it loads the compiz (core) plugins but it stucks in:
....
[COLOR=#008000]acer@acer-Aspire-4730Z:~$ unity
stop: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
start: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
[/COLOR][COLOR=#ff0000]Segmentation fault (core dumped)[/COLOR]

This happens when I write 
[COLOR=#008000][I]Unity
Setsid Unity
Unity --replace[/I][/COLOR]

There's a very limited info about this one and posts offer what I already did. Im sorry I cant put the complete tty info as Im posting this from my phone ...thanks in.advance!! I really need some.files and pretty much tried everything out there! :(

---

### Post by CantankRus on 2015-07-29
If you need to access your files quickly, install another desktop that doesn't use compiz.
From the greeter log into tty1 (ctrl+alt+F1) and install gnome-session-flashback...
```
sudo apt-get install gnome-session-flashback
```

Once installed press ctrl+alt+F7 to get back to the greeter.
Hit the icon to the right of your account name and
log into the "(Gnome Flashback (Metacity)" session.
If the session doesn't show at the greeter you may have to restart.

Also try running ...
```
sudo apt-get install ubuntu-desktop
```

Any errors when you run an update?
```
sudo apt-get update && sudo apt-get upgrade  
```

---

### Post by Aisiv on 2015-07-29
Hmm nope, not working. When I login with the option, screen remains the same. Even if I run nautilus (which is the only way to see my files[loads the icons but not the unity or compiz and I have full access]) it wont recognize/access to /media/ which is the external disk or USB where I want to backup my files in. With nautilus I am only limited to see and access files.
I can run firefox with TTY but I can not switch between windows, the plugins seem to be okay, I can see videos and all.
Update and Upgrade work fine but wont solve the issue :(

---

### Post by CantankRus on 2015-07-29
You don't have a live ubuntu usb or cd to use which should allow you to attach a mem stick for backup?

---

### Post by Aisiv on 2015-07-29
unfortunately nope, Im afraid that files (very tiny ones) can be damaged. I need to rescue about 150GB but urgent just about 6.

---

### Post by CantankRus on 2015-07-29
150gb ....and you didn't have backup? #-o
Odd that the flashback session won't even work.
Other than go to your local newsagency and get a magazine with a live cd, 
I don't really know how to solve assuming you have tried the grub recovery options.

If your willing to take the risk and had a live cd/usb, you could [**_[COLOR="#B22222"]reinstall while preserving home[/COLOR]_**]("https://help.ubuntu.com/community/UbuntuReinstallation").

---

### Post by Aisiv on 2015-07-29
Haha I know, actually this is the backup; the original files were from a windows OS that was entirely ruined. I have 2 options: using the Hard Drive as   External in another PC which is my last resource and format, and the live ubuntu usb. I'll wait to see if I can do the first one, tho. Thanks for your help! I'll see if someone else pops up with some more ideas

---

