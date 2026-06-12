---
title: "Installed update: now desktop won't load"
date: 2013-06-02
forum: Desktop Environments
---

### Post by jdlobb on 2013-06-02
I just installed an update to ubunto using the system update program and restarted the computer.  But when it booted it loads a 640x480 screen with just thedesktop background.  At first i get the "enter password for keyring 'default' to unlock" box that prompts me for my password.  after i put in my password and the box goes away I'm left with just the background image and a cursor.

If i right click i get the "new folder, new document, etc." menu and i can left click and create a selection box.  but other than that, i can't do anything.  There's no toolbar, no icons, nothing.

please help.  i have no idea what to do and i can find anybody with a similar problem through google.

edit:
I did some more searching and came across as possible solution, though the problem described said they had a black screen and a cursor.  So i ran the following commands 

sudo apt-get remove compiz      
sudo apt-get remove compiz-core       
exit

and rebooted

when the computer booted there were 2 error boxes that were so small the txt was illegible, i pressed enter and they went away.

The screen resolution is still 640x480, but now i see the regular login screen with the toolbar at the top and the option to log in as myself, guest, or remote.

but when i enter my password i get the following error box

Failed to load session "ubuntu" and a "log out" button

clicking the button makes the screen flash a couple times then takes me back to the log-in screen

---

### Post by jdlobb on 2013-06-02
update: i uninstalled and reinstalled the nvidia drivers

the resolution is now back to normal, but i still don't have a toolbar at the top or icons on the side.  if i right click i can go to "change desktop background" and it opens the system settings.  but i still have no way to open anything else.


edit:

ran the following

sudo apt-get install dconf-tools     
dconf reset -f /org/compiz/


get the following error
error: Error spawning command line 'dbus-launch --autolaunch=e31a66081e0af322tc975f51a53887 --binary-syntac --close-stderr ': Child process exited with code

Usage:
   dconf reset [-f] PATH

Reset a key or dir. -f is required for dirs.

Arguments:
  PATH     Either a KEY or DIR
  KEY      A key path (starting, but not ending with '/')
  DIR      A directory path (starting and ending with '/')


soembody please please help!

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]jdlobb; Hi !

A bit more info to enable us to help you:
What version and distribution do you have installed ?
Please submit the output of terminal codes:
```
lsb_release -a
uname -r

```
and is this install a "standard" installation from a desktop install medium  ?

Just so we know where you are coming from.
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by grahammechanical on 2013-06-03
Do you want to know what you did wrong?

> [COLOR=#000000]sudo apt-get remove compiz [/COLOR]
[COLOR=#000000]sudo apt-get remove compiz-core[/COLOR]

You removed the compositor/window manager that Ubuntu uses to create a desktop with the Unity user interface. I am assuming that you are using standard Ubuntu Unity and not a flavour of Ubuntu. There is no need to remove Compiz. It is possible to install alternative desktop without removing either Compiz or Unity. We certainly should not remove either of them without first installing an alternative.

You can try at the login screen to open a terminal by pressing Ctrl+Alt+F2 and then installing Compiz with

```
sudo apt-get install compiz-core
```
```
sudo apt-get install compiz
```

Then reboot by running

```
sudo shutdown -r now
```

If you then get to a desktop without the top panel or the launcher - right click the desktop and select Change Desktop Background. That will open System Settings. If you are using 13.04 open Software & Updates and go the the Additional Driver tab and experiment with video drivers.

Once you get a video driver that works go into Additional Drivers again and under the Ubuntu software tab untick Proprietary Drivers (restricted) and then the proprietary video driver will not be updated and will not cause this problem again (hopefully)

Regards.

---

