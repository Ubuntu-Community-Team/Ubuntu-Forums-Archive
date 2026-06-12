---
title: "Xbox 360 Wired or Wireless Issue"
date: 2014-04-10
forum: Gaming &amp; Leisure
---

### Post by danjalical on 2014-04-10
Afternoon/Morning

I apologise in advance if this is not the right place, but I have been having issues with this and after a week I am no better at it.  I am trying to use a Xbox 360 controller on my Ubuntu 14.04 (upgraded from 13.10) Laptop.  It is an Asus ROG G750jw and so far I have everything work really well.  What I am having trouble now is trying to get the 360 controller to work.

I have gone threw the guide to install Xboxdrv and it does detected the device.  At first I was using the wireless version and what would happen is the device would be found by Xboxdrv and display it as wireless but when I would try to use jstest it too would detect the device, however it would show no response if I pushed any buttons, or If I tried to move any of the controllers.  I loaded up steam, which detected it in the sense that it displayed the xbox buttons on big screen mode but again, no life.  

I bought a wired version, thinking that it may have better compatibility with Ubuntu, it does the exact same symptoms as the wireless version. My last effort is to install a usb live disc and see if maybe one of my many changes (i have installed play onlinux as well as a wallpaper changer) may have cause some background issue.

If you could point me in the right direction, or ask of me some kind of 'print out' that I could give you to help me diagnose my situation I would be much appreciative.  If however you are as stumped as me, and I can not solve this, it is no big issue.. its just something minor I would like to have working as I'm not one for giving up.

Alternatively if you could even recommend a better Ubuntu compatible game pad I would even go for that as well.

I thank you for your time,


Daniel.

---

### Post by Kirboosy on 2014-04-10
Did you disable the xpad module from being loaded?

```
sudo rmmod xpad
```

Also is the Xboxdrv program running?

```
sudo xboxdrv --silent
```

Once you do those two things fire steam back up and see what happens!

Hope that helps!
~Caboose
PS you can also install the following packages to test and calibrate the device
```
sudo apt-get install jscalibrator libgii1 libjsw2
```

---

### Post by danjalical on 2014-04-10
I have gotten home and have tried what you asked, firstly I did ensure that xpad was not loading.  Infact I couldn't find running, and it wasn't installed.  I did try the jscablibrator.. however this package didn't exist.  Something intersting however has occured.  

When I use my wireless reciver I do get this  
```

Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          003:015
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js4
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output


```

Yet nothing happens.. even if move the buttons or triggers.  This is how it has been since the begining of the week.

 however, if I stop the program, unplug and then replug the wireless adapter and then move the joystick buttons when I load the program  this will start happening
```

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          003:016
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js4
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
X1:   375 Y1:  4717  X2:  -128 Y2:  -383  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1:  7973 Y1: 11619  X2:  -128 Y2:  -383  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1:  7973 Y1: 17331  X2:  -128 Y2:   125  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1: 19239 Y1: 21496  X2:  1792 Y2:   125  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1: 23955 Y1: 24828  X2: 10368 Y2:  4443  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1: 24741 Y1: 27803  X2: 10368 Y2:  7618  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1: 24741 Y1: 27803  X2: 16896 Y2: 11428  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0

```
The device springs to life, and is usable and works flawlessly in full screen mode on steam as well as a few emulators I have.

I am not sure what kind of bug could cause this, but I hope this does help sombody.  Also, on my laptop I have noticed the top left usb will turn the device to be 'controler one' indicated on the game pad, if I use the right side it will light up as 'controler 2'  I am sorry that I am not giving any technical advise, but I hope this does help sombody or shed light into what could cause this.

---

### Post by Kirboosy on 2014-04-10
It sounds like the pairing of the wireless controller isn't working quite right. Bumping the power seems to straighten it out though. 

Perhaps changing ports without killing the service tricks the computer into thinking two seperate game pads are in use? Try stopping xboxdrv before replugging in to a new port. See if that eliminates the issue.

Hope that helps!
~Caboose

---

### Post by danjalical on 2014-04-10
I have done what you have asked this is the exact ternminal read out

danjalrog@danjalrog-G750JW:~$ sudo xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          003:007
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
^CShutdown complete
danjalrog@danjalrog-G750JW:~$ sudo xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          003:008
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
X1: -4472 Y1: 32767  X2:   256 Y2: -3685  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:

Again if like magic, the device will not work, however as you can see from the termal read out, if i stop the program, unplug the device, replug the device and move the buttons as I start the program, it works right away. 

I have also rebooted the machine to start fresh and i have the same issue.  I guess its a strange kink in my system.  My hope is that while I don't understand why this is happening sombody may, or it may help sombody else who is having a similar furstartion with a xbox controller.

I'm unsure to mark this as solved.. as while it is working every time, I'm not sure why.

---

### Post by Kirboosy on 2014-04-10
Now that you got the wireless controller working does the wired controller have the same issue?

~Caboose
PS.[ Marking a post Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by danjalical on 2014-04-10
```
danjalrog@danjalrog-G750JW:~$ sudo xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Controller
Vendor/Product:    045e:028e
USB Path:          003:011
Controller Type:   Xbox360

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
^CShutdown complete
danjalrog@danjalrog-G750JW:~$ sudo xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Controller
Vendor/Product:    045e:028e
USB Path:          003:011
Controller Type:   Xbox360

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
^CShutdown complete
danjalrog@danjalrog-G750JW:~$ sudo xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Controller
Vendor/Product:    045e:028e
USB Path:          003:012
Controller Type:   Xbox360

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event12

Press Ctrl-c to quit, use '--silent' to suppress the event output
X1:   832 Y1: 23190  X2: -2607 Y2: -1378  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0
X1:   832 Y1: 29216  X2: -2607 Y2: -1378  du:0 dd:0 dl:0 dr:0  back:0 guide:0 start:0  TL:0 TR:0  A:0 B:0 X:0 Y:0  LB:0 RB:0  LT:  0 RT:  0


```
This is from the wired controller.  It has the exact symptom of the wireless version... 

The first is me plugging it normal moving the buttons, the second is me stopping the program and NOT removing it but moving the buttons as I restart it and it shows nothing.  The third time is me unplugging it and plugging it, pushing the buttons as I restart the program and as you can see it springs to life.  Bare in mind I start the program relatively quickly after I have plugged the device in. 

I hope this is helpful to somebody other than myself.

---

