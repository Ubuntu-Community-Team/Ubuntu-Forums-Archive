---
title: "joy2key"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by nzadLithium on 2007-12-26
hey 

i've been playing around with the joy2key program for a few days. The version in the ubuntu repo's in my opinion sucks. No offence meant to the ubuntu team but it must have modified source from the joy2key package at the maintainers website. The ubuntu version keeps sending shift events with everything. (Its a real pain. I decided i wanted to see if i could get joy2key to open stuff on the desktop but every time i tell it to move to an icon it selects a bunch of icons!!!)

So i decided to get the maintainers version. I downloaded and then ran ./configure make and it gave me a whole bunch of errors about how it couldnt find various parts of xlib. So i compiled like this 
gcc joy2key.c -o joy2key-bin -lX11

and then it compiled nicely :D

I can now send keyboard events fine. The only problem i have with the keyboard events right now is it sends too many. Instead of moving from the icon i have it on to the next one, it zooms from the icon i have it on to the other side of the screen!!! any ideas on how to slow it down??

Also i'm trying to get it to move the mouse pointer as well. So i opened up keysymdef and i started looking for mouse events.

All of these seem to be mouse events ```
#define XK_Pointer_Left                  0xfee0
#define XK_Pointer_Right                 0xfee1
#define XK_Pointer_Up                    0xfee2
#define XK_Pointer_Down                  0xfee3
#define XK_Pointer_UpLeft                0xfee4
#define XK_Pointer_UpRight               0xfee5
#define XK_Pointer_DownLeft              0xfee6
#define XK_Pointer_DownRight             0xfee7
#define XK_Pointer_Button_Dflt           0xfee8
#define XK_Pointer_Button1               0xfee9
#define XK_Pointer_Button2               0xfeea
#define XK_Pointer_Button3               0xfeeb
#define XK_Pointer_Button4               0xfeec
#define XK_Pointer_Button5               0xfeed
#define XK_Pointer_DblClick_Dflt         0xfeee
#define XK_Pointer_DblClick1             0xfeef
#define XK_Pointer_DblClick2             0xfef0
#define XK_Pointer_DblClick3             0xfef1
#define XK_Pointer_DblClick4             0xfef2
#define XK_Pointer_DblClick5             0xfef3
#define XK_Pointer_Drag_Dflt             0xfef4
#define XK_Pointer_Drag1                 0xfef5
#define XK_Pointer_Drag2                 0xfef6
#define XK_Pointer_Drag3                 0xfef7
#define XK_Pointer_Drag4                 0xfef8
#define XK_Pointer_Drag5                 0xfefd

#define XK_Pointer_EnableKeys            0xfef9
#define XK_Pointer_Accelerate            0xfefa
#define XK_Pointer_DfltBtnNext           0xfefb
#define XK_Pointer_DfltBtnPrev           0xfefc

```

so i run this ./joy2key-bin -rcfile /home/cmaster/.joy2keyrc -axis Pointer_Right Pointer_Left
i then move the joystick axis left (which will move the pointer right :D) but nothing happens. 
When joy2key asked me for a window to send x events to i selected the desktop. Is this not the right place to send it to to move the mouse pointer?

So my two questions really are how do i move the mouse pointer and how do i make the autorepeat on joy2key lower. I have tried setting auto repeat = 1 which would theoretically make it send one button press event per second??

---

### Post by win32blows on 2007-12-27
Might wanna check out qjoypad , I use that with my PS2 controller if my mouse dies on me.

---

### Post by nzadLithium on 2008-01-03
i got qyoypad_3.4-1_i386.deb when i try to run it i got dependency problems. When i looked on net it said not to worry and just force it to install. So i did that. Qjoypad runs fine but as long as qjoypad is installed it breaks the auto update. I'm wondering if you managed to get it to work without causing problems?

---

### Post by ekimregnirps on 2008-01-05
[http://freshmeat.net/projects/js2mouse/](http://freshmeat.net/projects/js2mouse/)

---

### Post by fnf on 2008-01-13
> **nzadLithium said:**
> i got qyoypad_3.4-1_i386.deb when i try to run it i got dependency problems. When i looked on net it said not to worry and just force it to install. So i did that. Qjoypad runs fine but as long as qjoypad is installed it breaks the auto update. I'm wondering if you managed to get it to work without causing problems?

I attached a newly built qjoypad package. It is properly created (no checkinstall) so no worries.

---

### Post by GSF1200S on 2008-01-13
> **fnf said:**
> I attached a newly built qjoypad package. It is properly created (no checkinstall) so no worries.

Could you by some miracle create a 64bit version.. Ive been at war with dependencies for the last hour trying to make this work...

---

### Post by fnf on 2008-01-14
> **GSF1200S said:**
> Could you by some miracle create a 64bit version.. Ive been at war with dependencies for the last hour trying to make this work...

It is possible to use pbuilder to build a 64-bit package in a 32-bit system, but I have no 64-bit Linux around to test the package, so it may or may not work (no previous experience with 64-bit systems, I'm sorry).

qjoypad doesn't seem to be very active: there is no package even in 32-bit Ubuntu. I suggest you build one yourself, either:
[list][*]Install needed dependencies and **./config && make** . Then run the **./qjoypad** in the source directory directly, no installation needed.
[*]Install needed dependencies and build a proper deb package.[/list]

In the latter case, I've uploaded qjoypad with 'debian' directory. All you have to do is run '**dpkg-buildpackage -B -rfakeroot**' in the source directory (the one with 'debian').

You have to install **build-essential**, **autoconf**, **automake**, **fakeroot**, **dh-make** prior to the building. These tools are normally required to create DEB packages, along with the dependencies.

If you don't know about the dependencies of qjoypad, just try dpkg-buildpackage and look for the error message :-) .

---

### Post by GSF1200S on 2008-01-14
> **fnf said:**
> It is possible to use pbuilder to build a 64-bit package in a 32-bit system, but I have no 64-bit Linux around to test the package, so it may or may not work (no previous experience with 64-bit systems, I'm sorry).

qjoypad doesn't seem to be very active: there is no package even in 32-bit Ubuntu. I suggest you build one yourself, either:
[list][*]Install needed dependencies and **./config && make** . Then run the **./qjoypad** in the source directory directly, no installation needed.
[*]Install needed dependencies and build a proper deb package.[/list]

In the latter case, I've uploaded qjoypad with 'debian' directory. All you have to do is run '**dpkg-buildpackage -B -rfakeroot**' in the source directory (the one with 'debian').

You have to install **build-essential**, **autoconf**, **automake**, **fakeroot**, **dh-make** prior to the building. These tools are normally required to create DEB packages, along with the dependencies.

If you don't know about the dependencies of qjoypad, just try dpkg-buildpackage and look for the error message :-) .


Thanks, ill try this tonight. I actually managed to get qjoypad working, but it requires nearly 60 (!) packages to install and function, which is pretty bad. Apt then wouldnt update as it had dependency conflicts, and I had to remove qjoypad and all associated packages. This ended up attempting to remove my entire GUI (i removed a package in adept which doesnt tell you what its removing) as I built KDE with apt from the command line, and in order to stop it I had to control alt backspace out of adept. This of course left apt locked, so I had to reboot, reinstall the kdebase metapackage, then install the programs removed by adept, including adept itself.

As you can see, this little program has become an excercise in patience and a nightmare ](*,)

---

### Post by BryanFRitt on 2008-07-09
> **nzadLithium said:**
> hey 

I've been playing around with the joy2key program for a few days. The version in the Ubuntu repo's in my opinion sucks. No offense meant to the ubuntu team but it must have modified source from the joy2key package at the maintainers website. The Ubuntu version keeps sending shift events with everything. (Its a real pain. I decided I wanted to see if I could get joy2key to open stuff on the desktop but every time I tell it to move to an icon it selects a bunch of icons!!!)

So I decided to get the maintainers version. I downloaded and then ran ./configure make and it gave me a whole bunch of errors about how it couldn't find various parts of xlib. So I compiled like this 
gcc joy2key.c -o joy2key-bin -lX11

and then it compiled nicely :D
(capitalization and "'" edited)

I have the same problem with KUbuntu's8.04_64bit version of this sending shift with everything as well(at least with the few things that I've tried Konqueror, kate,...)

I've tried compiling joy2key but it gives undefined reference to
*XSendEvent XFlush XStringToKeysym XKeysymToKeycode XOpenDisplay XQueryTree XSelectInput XFree XFlush XCheckWindowEvent*
during make.

Now, I tried your command and running the new ./joy2key-bin file directly and it works!
*sudo ./joy2key-bin -X -thresh 0 255 0 255 0 255 0 255 -buttons Up Right Down Left -axis Left Right Up Down*
It comes with a sample config file, if you can find it.

Even though I got it working, I'm going to try out qjoypad  
[http://ubuntuforums.org/showthread.php?t=147918&page=2](http://ubuntuforums.org/showthread.php?t=147918&page=2)
Wish me luck.

---

