---
title: "Wine Issue/Bug MOHAA &amp; Mouse"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by dj3019 on 2007-05-28
Emulation in wine is pretty sticky.  I can open just about any windows file and installer but when running games the graphics blink in and out (Uplink) or the mouse doesn't stay within the window preventing (MOHAA) you from turning or accessing menus.  I've tried to compile the WineCVS to hopefully circumvent the issue but the compiler ends abruptly with an error about missing dll's.  During the dev package acquisition I was unable to get the following

"sudo apt-get install libgtk-1.2 libgtk-1.2-common" and it says that it is unable to locate the package

Someone please aide me!

---

### Post by mbradlcu on 2007-05-29
using 'winecfg' under the "Graphics" tab, make sure "Allow DirectX apps..." is checked. hope this helps

---

### Post by dj3019 on 2007-05-30
I have checked and unchecked the feature for DirectX control in the winecfg but it doesn't work for OpenGL games like MOHAA or Half-Life or Counter Strike.  I'm pretty sure these are all OpenGL.  Now the game runs fullscreen no hitches there.  Emulation is working but I have to run it with the sudo command otherwise it can't load the OpenGL libraries for the default.cfg.  once I run the command

sudo wine mohaa 

Emulation begins in fullscreen but in order to see the whole window for the game

So I run

gnome-session-remove gnome-panel 

then I run the sudo wine mohaa

Launches flawlessly it the mouse control that is weird.  It seems to start the cursor in the middle of the screen but MOHAA defaults to the top left.  By moving the cursor to the top-left and matching the background cursor to the in game cursor I can reset the system and have full control of the menus but once I'm in the game playing the mouse cursor defaults to the center and the floating pointer for Ubuntu is still not locked to the program.

Anymore ideas... I'm getting close I can just taste it!!!!

---

### Post by dj3019 on 2007-05-31
Okay... the fullscreen issues have been taken care of by using the command

gnome-session-remove gnome-panel

Uplink now plays without any flickers or mouse-over problems.

MOHAA- Still has issues with the mouse

Installed Star Wars Jedi Knight 2 - Jedi Outcast and it runs perfectly.

Understanding Level: Dangerously Low

--== UPDATE ==--

MOHAA WORKS!

After you install winecvs (not sure if it was that really) or wine and install the game there is one last thing you need to do.

Go to [http://www.3dgamers.com/dlselect/games/medalofhonor/Thirdparty/mohaa-lnxclient-beta3.tar.bz2.html](http://www.3dgamers.com/dlselect/games/medalofhonor/Thirdparty/mohaa-lnxclient-beta3.tar.bz2.html) and download the linux client.

Now it is very buggy and the only problem I've had so far is that clicking quit locks up the system and I am forced to hold the power switch.  Other than that it fixes just about everything.  I can finally play!

---

