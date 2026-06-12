---
title: "Can't Log out of KUbuntu - KDE"
date: 2008-06-29
forum: Desktop Environments
---

### Post by BryanFRitt on 2008-06-29
I can't log out of KDE.  I can try a log out but all I get i a blank screen with a mouse pointer I can move around.
Could this be from a recent update?  
Last update I remember was an update in wine 1.0 to wine 1.1.
I had a wine application running during this update,
Since I've gotten this error I've tried uninstalling wine and rebooting,
it still doesn't log out.
I can do a alt+ctrl+Backspace to get to the login screen,
I've noticed it doesn't save my icon arrangement changes though.
I've also tried unplugging my external devices and exiting from all the applications in the tray.
Nothing so far has worked.
I tried doing a recovery boot(or whatever it was called) with repair x-config, didn't work (had to reinstall NVidia drivers though)
Any ideas?
Could this have been caused by a resent update?
I can't recall messing with anything technical.
Oh.. I also tried the weird bug on my system where gnome desktop will appear(on desktop 1?) when I try the hide desktop icons option(right click on desktop->Configure Desktop->Behavior->Show Icon on Desktop) then trying to log out again, still didn't work. (p.s. I don't have gnome installed)
Is there a log I can look at to see some kind of message as to why I can't log out?

---

### Post by Spaceman9 on 2008-06-29
If you click on System, Administration, System Log you can look at all of the logs in your Ubuntu install. This sounds like something that might only be fixable by reinstalling Ubuntu. I'm not sure though. Someone else night know how to fix your problem at the command line. Good luck.

---

### Post by BryanFRitt on 2008-06-29
going to kmenu->System->KSystemLog - System Log Viewer in 
Stuff logged about the time I logged out and had to use Ctrl+Alt+Backspace to finish logging out.

ACPI Log:

06/29/2008 04:56:10 PM	none	1 client rule loaded

06/29/2008 04:56:10 PM	none	client connected from 24388[0:0]

06/29/2008 04:56:11 PM	none	1 client rule loaded

06/29/2008 04:56:11 PM	none	client connected from 24388[0:0]

System Log:

06/29/2008 04:56:10 PM	************	kdm[5992]	StartServerSucces

06/29/2008 04:56:10 PM	************	kdm[5992]	X server for display :0 terminated unexpectedly

06/29/2008 04:56:10 PM	************	kdm[5992]	X server terminated: [0, 0, 0]

06/29/2008 04:56:20 PM	************	hcid[6609]	Default authorization agent (*****, /org/kde/kbluetooth**********) registered

06/29/2008 04:56:20 PM	************	hcid[6609]	Default passkey agent (*****, /org/kde/kbluetooth*****) registered

06/29/2008 04:56:20 PM	************	NetworkManager	<info>  Updating allowed wireless network lists. 

06/29/2008 04:56:21 PM	************	blueproximity[24742]	started.



Replacing all stuff that I suspect that I'm not supposed to show online with *. If there is anything else I'm not supposed show online, tell me.
Looks like this is stuff that occurred on on reloging in after ctrl+alt+backspace

---

### Post by BryanFRitt on 2008-06-29
Just found my notes from the first time I think this happened...
I did see an error type message the first time...
expected keysym, got XF86kbd ___ line 70
it said that for a bunch of different XF86xbd line numbers were 70,71, or 72
The XKEYBOARD keymap compiler (xkbcomp) reports
>Warning type "ONE_LEVEL" has 1 levels but <RALT> has 2 sympbols
Ignoring extra symbols
Errors form xkcomp are not fatal to the x server
xinit: connection to x server lost

I had tried to shutdown my computer overnight, left it before it finished shutting down.  And came back the next day and found these error messages.

These messages look like stuff that might have happened when I changed the volume keys to go by 2% instead of 10% volume changes.  I have a Dell Latitude D830.  Could this have anything to do with why I can't log out now?  I'm not getting this error message now though.

---

### Post by Spaceman9 on 2008-06-29
Really I don't know for sure. I don't see why changing the volume key setting should keep you from logging out. It sounds like not letting the OS shut down by it's self might have corrupted a config file.

I don't know any way to fix this except reinstall but that's just me. Waite and see what someone else says. There might be a fix for this that I don't know about.

---

### Post by BryanFRitt on 2008-06-30
It's fixed: I used apt-get to remove software with the word 'key' that I thought could have been the ones that gave the error from above and then rebooted trying an older kernel.  That fixed it! Shutdown and tried rebooting with the current default kernel (not the one I had just used), and it is still fixed.  Not sure which (or all) of the above fixed it.  (also wondering if I just didn't wait long enough before)  And the keyboard volume keys still go by 2% like I prefer (over the default 10% option).

---

### Post by BryanFRitt on 2008-07-21
Somehow the volume up/down got back to doing units of 10 instead of two, so I tried installing some programs that mess with keys... and guess what I can't log out again!  This time, I took a picture of what occurred after one time...


text from picture typed by hand
(==) Log file:"/var/log/Xorg.0.log", Time: Mon Jul 21 22:28:45 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Module "ramdac" already built-in
expected keysym, got XF86kbdLightOnOff: line 70 of pc
expected keysym, got XF86kbdBrightnessDown: line 71 of pc
expected keysym, got XF86kbdBrightnessUp: line 72 of pc
expected keysym, got XF86kbdLightOnOff: line 70 of pc
expected keysym, got XF86kbdBrightnessDown: line 71 of pc
expected keysym, got XF86kbdBrightnessUp: line 72 of pc
expected keysym, got XF86kbdLightOnOff: line 70 of pc
expected keysym, got XF86kbdBrightnessDown: line 71 of pc
expected keysym, got XF86kbdBrightnessUp: line 72 of pc
expected keysym, got XF86kbdBrightnessDown: line 149 of inet
expected keysym, got XF86kbdBrightnessUp: line 150 of inet
expected keysym, got XF86kbdLightOnOff: line 153 of inet
expected keysym, got XF86kbdBrightnessDown: line 154 of inet
expected keysym, got XF86kbdBrightnessUp: line 155 of inet
expected keysym, got XF86Info: line 914 of inet
xinit:  Connection to X server lost.

p.s. I have a Dell Latitude D830 computer

---

### Post by BryanFRitt on 2008-07-22
and also some of my keyboards shortcuts to KMenu item don't work unless I edit them again, (even to same values will fix it)

---

### Post by BryanFRitt on 2008-07-22
Looking a KDE System Guard->Process Table->Search: key, I have

gnome-keyring-d
keytouch-acpid
keytouchd
keytouchd
keytouchd
keytouchd
keytouchd-launc

I kill all the keytouchd ones, and I CAN LOG OUT, leave one keytouchd one, and I CAN't LOG OUT.  So, **the program preventing me from logging out is _keytouchd_!**

I try
*keytouch-editor*
 and get
[FONT="Courier New"]keytouch-editor: No event devices are available in /dev/input/.[/FONT]
So I try
*sudo keytouch-editor*
 and get a program
 Don't feel like messing with it so I'm going to remove it:keytouch,keytouch-data, keytouch-editor
doing that leaves keytouchd-launc running.

After rebooting, the VolumeUp/VolumeDown keys go by 10 instead of 2.
I'd rather be able to log out and use those keys as +-10 instead not being able to log out and those keys functioning as +-2.
 
Is there another program or command line that I could use to adjust the volume change rate?

p.s. I have win+E set to launch Konqueror, but it doesn't work anymore unless I edit the shortcut in KMenu (edit it to blank and then back to win+E, save).  The other shortcuts seem to still work without having to do this to them.  Any ideas?

---

