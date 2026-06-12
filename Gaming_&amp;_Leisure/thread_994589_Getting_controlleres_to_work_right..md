---
title: "Getting controlleres to work right."
date: 2008-11-26
forum: Gaming &amp; Leisure
---

### Post by Arukas on 2008-11-26
First off, has anyone acutally resently gotten the xbox 360 usb controller to work for ubuntu?  I'd read the forums, and nothing works, plus nothing seems current either.

Second, I have a logitech pc gamepad.  I"d read tutorials, download programs, but Ubuntu don't want to reconize the joystick correctly.  (It looks like a PS2 controller)  It doesn't reconize the directional pad, everything has to be done on the joystick, and that's not very user friendly.

Anyone gotten controllers to behave correctly?

---

### Post by crazyfuturamanoob on 2008-11-27
I soldered an old xbox controller's cable myself, and got it working with my Hardy.

Every button works with joy2key and jscalibrator. Even the triggers.

I have been playing AlephOne with this. It's the best way to play it, far more accurate than keyboard & mouse.

---

### Post by Arukas on 2008-11-27
I have both those programs.  I calibrated the xbox 360 controller.  However, joy2key doesn't work at all.  It says this

joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.1   Binary built on Oct 30 2007 at 08:10:20

Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

---

### Post by Frem on 2008-11-27
I believe you need the xpad driver.

I forget what forum member I got this script from, but it works.

> mkdir $HOME/joystick
cd $HOME/joystick
wget "http://www.horza.info/projekti/xpad-driver-linux/xpad.c"
wget "http://www.horza.info/projekti/xpad-driver-linux/xpad.h"
wget "http://www.horza.info/projekti/xpad-driver-linux/Makefile"
sudo modprobe -r xpad
make
sudo make install
sudo modprobe xpad
cd $HOME
rm -Rf $HOME/joystick

Paste it into a text file and save it. Right click on the file and select properties. Click on the permissions tab, and check the "Allow executing file as program" box. Double click on the file and "Run in Terminal".

After this, your joypad will work. Unfortunately, the driver won't load automatically after you reboot. Just open a terminal and type "sudo modprobe xpad" after each time you reboot to reload the driver.

You may also need to install and modprobe "joydev", I'm not sure.

---

### Post by Arukas on 2008-11-28
Xpad, I've known I tried to install xpad before.  What's the deal with it not loading correctly?  I appreicate the help, but it sounds like a lot of guess work.  Exactly, the same as some of the tutorials I've in these forums.  

I know I modified a file to start something up when Ubuntu boots.  Why is Ubuntu not joystick friendly?

---

### Post by Arukas on 2008-11-30
I still have not figure out how to get my controllers to work, and the tutorials are not being helpful.

---

### Post by grossaffe on 2008-11-30
I tried a USB 360 controller in ubuntu and it worked without any fuss.

---

### Post by Arukas on 2008-11-30
Do you actually use it?  I can plug mine in and calibrate it.  joy2key don't work for it, and it says I don't have any joysticks plugged in.  The d-pad and joysticks aren't reconized right, it does some weird stuff. 

Also, my pc game controller has the same fuss.  



What did you do to install it?  What do you use it for too?  Its a nice controller and I would like to figure out

---

### Post by grossaffe on 2008-12-01
> **Arukas said:**
> Do you actually use it?  I can plug mine in and calibrate it.  joy2key don't work for it, and it says I don't have any joysticks plugged in.  The d-pad and joysticks aren't reconized right, it does some weird stuff. 

Also, my pc game controller has the same fuss.  



What did you do to install it?  What do you use it for too?  Its a nice controller and I would like to figure out

I used it for an SNES emulator.  All I did was plug it in and it worked for me.  No need to mess with anything.  Perhaps I did everything necessary to get it work earlier when setting up a logitech controller.  I think for that one I installed jstest.

---

### Post by ColeJayStooks on 2008-12-02
Would anyone know how to get a Gamecube controller working or did they work that in the kernel or something when I wasn't looking?

---

