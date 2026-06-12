---
title: "Booting KDE"
date: 2005-08-11
forum: Desktop Environments
---

### Post by blinky on 2005-08-11
](*,) 

Hey,
I'm using Kubuntu for the first time after previously trying SuSe 9.3 (my first distro - which I did like but was a bit tricky to install things).

I've installed Kubuntu fine and it boots up but after this I get confused. The user login screen and afterwards is a (white on black) command line interface. It logs in ok fine but doesn't load KDE like I would assume it should. After login the command line interface just says:
user@pcname :~$

Is there something I need to setup from this point or have I screwed it up already?

Any help appreciated,
thanks

---

### Post by Lord Illidan on 2005-08-11
Did you load up the fail-safe Ubuntu or the normal Ubuntu? On my boot up list, the normal Ubuntu is first on the list.
The fail-safe Ubuntu gives you a console log-in.

Also, you might want to give us the contents of your /etc/X11/xorg.conf , maybe you have bad graphics drivers.

Third, if you do ```
sudo startx
```, does x start?

---

### Post by gingermark on 2005-08-11
It sounds like the Window Manager isn't set up properly. It should start KDM and present you with a graphical login screen.

I had a similar problem with Ubuntu when I upgraded to Hoary, but someone helped me out with that - I can't remember exactly what is to be done, but I'm sure someone else will be able to tell you.

It would probably help though to mention what graphics card you are using, and if you did any manual setting up of the graphics during installation or not. Kubuntu would normally detect and set up the graphics automatically, but obviously it didn't in this case, so I guess the thing is to figure out why.

---

### Post by Lord Illidan on 2005-08-11
Also, did you install in expert or normal configuration?

---

### Post by blinky on 2005-08-11
> Did you load up the fail-safe Ubuntu or the normal Ubuntu? On my boot up list, the normal Ubuntu is first on the list. 

No i booted the normal version - yep the top of the list.


> sudo startx 

It tried to run but didn't work.

I can tell you what it says on the screen but not what flew off the top:
"
You need to have Glide installed to run the glide driver for XFree86. Also, you need to tell XFree where libglide2x.so is placed by making a soft link in the /usr/X11R6/lib/modules directory that points to libglide2x.so file. For example (if your libglide2x.so file is in /usr/lib0:
   # ln -s /usr/libglide2x.so /usr/X11R6/lib/modules


(EE) Failed to load module "glide" ...
(EE) No drivers available

Fatal server error:
no screens found

help available at [http://wiki.X.Org](http://wiki.X.Org)

X10: fatal IO error 104 ....
"

---

### Post by Lord Illidan on 2005-08-11
Glide? What graphics card do you have? One of those Banshees?

If so change the entry under Device in your /etc/X11/xorg.conf to "vesa"

This is mine : 

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]" -- Yours should be different!
        Driver          "nvidia" -- Change this to "vesa"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by blinky on 2005-08-11
[QUOTE=gingermark]It sounds like the Window Manager isn't set up properly. It should start KDM and present you with a graphical login screen.

I had a similar problem with Ubuntu when I upgraded to Hoary, but someone helped me out with that - I can't remember exactly what is to be done, but I'm sure someone else will be able to tell you.

It would probably help though to mention what graphics card you are using, and if you did any manual setting up of the graphics during installation or not. Kubuntu would normally detect and set up the graphics automatically, but obviously it didn't in this case, so I guess the thing is to figure out why.[/QUOTE]



Yeah looking at the output from the startx command it might seem to be that. ie. the 'no screens found' part.

The PC is pretty old but did work fine in SuSe so drivers may be available. 
It is an AMD K6-2 running on a PAG-2130 motherboard. There is a graphics accelerator in a PCI slot but I just can't remember what it is right now... hmm. I could bypass this and go straight from output from the motherboard.

---

### Post by blinky on 2005-08-11
[QUOTE=Lord Illidan]Glide? What graphics card do you have? One of those Banshees?

If so change the entry under Device in your /etc/X11/xorg.conf to "vesa"

This is mine : 

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]" -- Yours should be different!
        Driver          "nvidia" -- Change this to "vesa"
        BusID           "PCI:1:0:0"
EndSection[/QUOTE]


How do you edit a file when you only have a command line interface? Never done this although i'm sure it's very simple.

---

### Post by Lord Illidan on 2005-08-11
I should have told you before, I apologise..

you simply type

First backup the xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` 

This will copy the xorg.conf to another newly created file called xorg.conf_backup, which you can use if the original xorg.conf gets damaged. Always make it before you carry out a major/minor change!

```
sudo vi /etc/X11/xorg.conf
``` 

This will open vi, a text editor.

To edit files, you have to press INSERT from your keyboard.

Then you can start typing in..

To quit press Escape, and a colon should appear at the bottom of the screen. Type wq to exit.

---

### Post by blinky on 2005-08-11
[QUOTE=Lord Illidan]I should have told you before, I apologise..

you simply type

First backup the xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` 

This will copy the xorg.conf to another newly created file called xorg.conf_backup, which you can use if the original xorg.conf gets damaged. Always make it before you carry out a major/minor change!

```
sudo vi /etc/X11/xorg.conf
``` 

This will open vi, a text editor.

To edit files, you have to press INSERT from your keyboard.

Then you can start typing in..

To quit press Escape, and a colon should appear at the bottom of the screen. Type wq to exit.[/QUOTE]



Woohooo its loading KDE :)

My uni tutor thought i'd might be the same problem although suggested using:
> sudo dpkg-reconfigure xserver-xorg 

Knowing what most of the hardware is and a couple of guesses it seems to be loading.

*filcks back to Kubuntu*
Yep its loaded. So the X-Server setup was the problem and I guess the reconfigure command edited the xorg.conf file without manual editing.

Thanks :)

You didnt have to appologise for not mentioning how to edit a file, I just have never done it before, but now I know :)


Thanks for the help, much appreciated.

---

