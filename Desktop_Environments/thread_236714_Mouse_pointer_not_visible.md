---
title: "Mouse pointer not visible"
date: 2006-08-15
forum: Desktop Environments
---

### Post by digTro on 2006-08-15
I'm booting from the Dapper live CD. The mouse is working; the menus are becoming active if the mouse if over them and I can open them by clicking, but the mouse pointer is not visible. 

I have an nvidia gfx card and after [googling ]("http://www.google.co.in/search?q=mouse+pointer+invisible+in+ubuntu&hl=en")I found that some users with nvidia gfx card were having a similar problem. Then I came across this [HOWTO on installing nvidia drivers]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"). There it is mentioned that:

> 9) If (after installing the Nvidia driver) you are not able to see your mouse cursor or it blinks and this bothers you try this:

Add the following options to the Section Device of your xorg.conf:

Option "HWcursor" "Disabled" 
Option "SWcursor" "Enabled"

I followed the HOWTO and installed the nvidia package and have added the above options  but still the problem persists.

Any suggestions?

---

### Post by digTro on 2006-08-19
*bump*

---

### Post by plugitin on 2006-08-29
Yes I have the same exact problem. 

First I couldn't get drivers to work, but once I did, I could not see the mouse.

I have an Nvidia eVGA 6800GS graphics card and a Logitech Cordless Click! Optical Mouse. I can interact with things, but the pointer does not show up, and it is really frustrating to have to press Ctrl every time I want to click something.

Someone please help.

P.S. this is my first time using Linux

---

### Post by Kossilar on 2007-01-08
I'm having the same problem on the Edgy CD. My mouse cursor is invisible and I'm using a Geforce 6800GS.

The Edgy CD also sometimes fails to load the graphics properly, so my screen is all distorted and wierd.

---

### Post by Just_me on 2007-01-12
Did bump in to the same issue after completing the 6.10 installation.
Gfx card is a nv 6800 GS and mouse is a Logitech G7.

The cursor tweak works for me but with a slightly different syntax.

The entry should go in to the Device section where the gfx card is specified.
The HWCursor option takes a boolean as parameter (there is no need to specify both HWCursor and SWCursor).

xorg.conf has the following entries for my Gfx card and Mouse

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        VideoRam        262144
        Option          "HWCursor" "Off"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Hope this helps.

Side note: Did run into some display issue's during the install process, my screen was completely messed up after the splash screen (once X was started).
So I couldn't start the initial install process. The console seems not to be affected by this (at least not during the install), changing the color depth from 24 to 16 in xorg.conf solved this.

After finishing the install  the same issue occurred on the frame buffer console and when X was started. Adding vga=791 to the kernel boot options in /boot/grub/menu.conf and changing the color depth to 16 in /etc/X11/xorg.conf did solve it (vga=791 is 1024x768 16bits).


\

---

