---
title: "UT 2004 installed, but can't get it to start"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by threethirty on 2006-02-01
ummmmm.... yeah.... I (with the help of a buddy) got it installed, but now I can't get it to run.  I've been looking for an icon to click on but I'm thinking that is the way to go.  At the end of the installation it said to type "ut2004" or something similar, but it never said where to type this.

---

### Post by audax321 on 2006-02-01
You have to type the command in the terminal or I think KDE calls it Konsole. It should be in the menu somewhere (I use Gnome so I have no clue). You should also be able to make a shortcut to it via the right-click menu on the Desktop (just put ut2004) as the command.

BTW, that command is assuming you installed ut2004 as root and it is located in /usr/bin.  If you installed elsewhere run the following command: sh /path/to/game/ut2004  (except if you make a shortcut for this I don't think you need the sh portion of the command, just in the terminal).

---

### Post by threethirty on 2006-02-01
here is my attempt

```
three@CondorV2:~$ /home/three/ut2004
bash: /home/three/ut2004: is a directory
three@CondorV2:~$ sh /home/three/ut2004
/home/three/ut2004: /home/three/ut2004: is a directory
three@CondorV2:~$ sh /home/three/ut2004/ut2004.sh
sh: /home/three/ut2004/ut2004.sh: No such file or directory
three@CondorV2:~$

```

---

### Post by audax321 on 2006-02-01
Alright, can you try typing: locate ut2004
and post the output? Or see if KDE has a search program to search the hard drive and search for ut2004... I'm guessing you installed it locally and you just need to find out where the file is. :)

---

### Post by audax321 on 2006-02-01
Try this:

three@CondorV2:~$ cd /home/three/ut2004
three@CondorV2:~/ut2004$ ./ut2004

and the game should run... Your command if your making a desktop shortcut or menu shortcut would be: /home/three/ut2004/ut2004  (there is no .sh after the executable name... its just ut2004)

---

### Post by threethirty on 2006-02-01
Ok, when I searched I found 
file:///home/three/ut2004/ut2004
file:///home/three/ut2004

then I clicked on the top one, and in the processes ut2004-bin is running and the splash comes up but then nothing.

---

### Post by audax321 on 2006-02-01
in order to see any diagnostic messages, you need to run it in Konsole.

So open up Konsole and run the commands:

change folder to the ut2004 folder:  cd /home/three/ut2004
run ut2004:  ./ut2004

---

### Post by Perfect Storm on 2006-02-01
run it through the terminal and report the output.

---

### Post by threethirty on 2006-02-01
```
three@CondorV2:~$ cd /home/three/ut2004
three@CondorV2:~/ut2004$ ./ut2004
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
three@CondorV2:~/ut2004$



```

and AI would you like me to stop to stop repeating all of this on ubuntugaming.org assumiong that you are one in the same?

---

### Post by Perfect Storm on 2006-02-01
nah, no harm done ;)

By any chance is your Graphic card setup?

---

### Post by livingtarget on 2006-02-01
Have a look and attach the ut2004.log that can be found in: /home/{your-user-name}/.ut2004/System/

It often tells you more clearly what's up.

---

### Post by threethirty on 2006-02-01
AI: Not beyond taking the defaults when I first installed I have an ATI Radeon 9550 so a driver may be a little hard to find

livingtarget: this is a little ugly but here it is
```
Log: Log file open, Wed Feb  1 08:48:57 2006
Init: Name subsystem initialized
L o g :   Y o u r   l o c a l e :   [ U T F - 8 ] . 
 
 L o g :   E n a b l e d   U N I C O D E   s u p p o r t . 
 I n i t :   V e r s i o n :   3 1 8 6   ( 1 2 7 . 2 9 ) 
 I n i t :   C o m p i l e d :   M a r     4   2 0 0 4   0 3 : 0 7 : 4 1 
 I n i t :   C o m m a n d   l i n e :   
 I n i t :   ( T h i s   i s   L i n u x   p a t c h   v e r s i o n   3 1 8 6 . 0 ) 
 I n i t :   C h a r a c t e r   s e t :   U n i c o d e 
 I n i t :   B a s e   d i r e c t o r y :   / h o m e / t h r e e / u t 2 0 0 4 / S y s t e m / 
 I n i t :   I n i : U T 2 0 0 4 . i n i       U s e r I n i : U s e r . i n i 
 I n i t :   B u i l d   l a b e l :   U T 2 0 0 4   B u i l d   U T 2 0 0 4 _ B u i l d _ [ 2 0 0 4 - 0 3 - 0 3 _ 0 2 . 4 2 ] 
 I n i t :   O b j e c t   s u b s y s t e m   i n i t i a l i z e d 
 W a r n i n g :   M i s s i n g   C l a s s   C l a s s   E d i t o r . T r a n s B u f f e r 
 L o g :   I n i t i a l i z i n g   O p e n G L D r v . . . 
 L o g :   b i n d i n g   l i b G L . s o . 1 
 L o g :   G l o b a l   M D 5 :   [ 3 9 8 6 c 4 7 7 4 f 8 6 c a b 1 5 5 f f 9 f 5 4 3 2 b 8 9 2 8 2 ] 
 L o g :   G a m e   c l a s s   i s   ' G a m e I n f o ' 
 L o g :   B r i n g i n g   L e v e l   E n t r y . m y L e v e l   u p   f o r   p l a y   ( 0 )   a p p S e c o n d s :   1 1 . 5 0 5 6 0 5 . . . 
 S c r i p t L o g :   G a m e I n f o : : I n i t G a m e   :   b E n a b l e S t a t L o g g i n g   F a l s e 
 L o g :   B r o w s e :   N v i d i a L o g o . u t 2 ? N a m e = P l a y e r ? C l a s s = E n g i n e . P a w n ? C h a r a c t e r = J a k o b ? t e a m = 2 5 5 
 L o g :   C o l l e c t i n g   g a r b a g e 
 L o g :   P u r g i n g   g a r b a g e 
 L o g :   G a r b a g e :   o b j e c t s :   3 2 7 8 2 - > 3 2 7 8 1 ;   r e f s :   3 3 9 6 1 9 
 L o g :   G a m e   c l a s s   i s   ' C i n e m a t i c G a m e ' 
 L o g :   B r i n g i n g   L e v e l   N v i d i a L o g o . m y L e v e l   u p   f o r   p l a y   ( 0 )   a p p S e c o n d s :   1 3 . 9 7 8 6 8 7 . . . 
 S c r i p t L o g :   G a m e I n f o : : I n i t G a m e   :   b E n a b l e S t a t L o g g i n g   F a l s e 
 L o g :   C r e a t e d   a n d   i n i t i a l i z e d   a   n e w   S D L   v i e w p o r t . 
 L o g :   A L A u d i o :   U s i n g   A L C _ E X T _ c a p t u r e   t o   r e c o r d   a u d i o . 
 L o g :   S E T   P L A Y E R ! 
 S c r i p t L o g :   N e w   P l a y e r   P l a y e r   i d = 1 6 2 7 0 e c 3 c 7 0 7 f a 3 7 8 3 8 7 b 1 5 3 6 8 c b 4 2 c 2 
 L o g :   T T S :   N o   o u t p u t   f i l e n a m e   s p e c i f i e d . 
 L o g :   E n t e r   S e t R e s :   8 0 0 x 6 0 0   F u l l s c r e e n   1 
 L o g :   O p e n G L 
 C r i t i c a l :   C o u l d n ' t   s e t   v i d e o   m o d e :   C o u l d n ' t   f i n d   m a t c h i n g   G L X   v i s u a l 
 
 E x i t :   E x e c u t i n g   U O b j e c t : : S t a t i c S h u t d o w n A f t e r E r r o r 
 E x i t :   E x e c u t i n g   U S D L C l i e n t : : S h u t d o w n A f t e r E r r o r 
 L o g :   W a i t i n g   f o r   f i l e   s t r e a m i n g   t h r e a d   t o   f i n i s h . . . 
 E x i t :   O p e n A L   A u d i o   s u b s y s t e m   s h u t   d o w n . 
 E x i t :   E x i t i n g . 
 L o g :   F i l e M a n a g e r :   R e a d i n g   0   G B y t e   5 6   M B y t e   5 3 8   K B y t e   4 6 3   B y t e s   f r o m   H D   t o o k   2 . 3 6 9 5 7 3   s e c o n d s   ( 0 . 7 6 3 4 9 1   r e a d i n g ,   1 . 6 0 6 0 8 2   s e e k i n g ) . 
 L o g :   F i l e M a n a g e r :   0 . 0 0 0 0 0 0   s e c o n d s   s p e n t   w i t h   m i s c .   d u t i e s 
 U n i n i t i a l i z e d :   N a m e   s u b s y s t e m   s h u t   d o w n 
 U n i n i t i a l i z e d :   L o g   f i l e   c l o s e d ,   W e d   F e b     1   0 8 : 5 0 : 1 2   2 0 0 6 
 
```

---

### Post by audax321 on 2006-02-01
If your graphics card isn't setup and you have either an ATI, nVidia, or Matrox there are instructions here: [https://wiki.ubuntu.com/BinaryDriverHowto/](https://wiki.ubuntu.com/BinaryDriverHowto/)

The 9550 is in there...

---

### Post by livingtarget on 2006-02-01
Yes it's definitly the video card that hasn't been set up yet (see: audax321's post on how to resolve it). GLX is the video card driver that does (3d) accelerated graphics I think.

---

### Post by threethirty on 2006-02-01
thanks guys/gals/others?

I'll let you guys know how that goes

---

### Post by threethirty on 2006-02-01
Here is what happens when I try the first two lines

```
three@CondorV2:~$ sudo apt-get install linux-686
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not installable
          Depends: libgtk-perl but it is not going to be installed
          Depends: libgtk-pixbuf-perl but it is not going to be installed
          Depends: fping but it is not going to be installed
          Depends: libevent-perl but it is not going to be installed
          Depends: libintl-perl but it is not going to be installed
  linux-686: Depends: linux-image-686 but it is not going to be installed
             Depends: linux-restricted-modules-686 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
three@CondorV2:~$

```
```
three@CondorV2:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not installable
          Depends: libgtk-perl but it is not going to be installed
          Depends: libgtk-pixbuf-perl but it is not going to be installed
          Depends: fping but it is not going to be installed
          Depends: libevent-perl but it is not going to be installed
          Depends: libintl-perl but it is not going to be installed
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
three@CondorV2:~$

```

sorry for the long post

---

### Post by audax321 on 2006-02-01
It's really odd that it wants you to install those packages. I know those shouldn't be required for linux-686. Have you tried installing the packages through Synaptic instead (System > Administration > Synaptic Package Manager)? Give that a try and make sure you hit the reload button before you search for and install the linux-686 and xorg-driver-fglrx packages.

Also, for the linux-686 step... you can install a number of packages like linux-386, linux-686-smp... it depends on what processor your computer is running. So make sure it is actually a 686 processor before you install it.

---

### Post by threethirty on 2006-02-01
I hate to do this but here is what I installed with their descriptions (because long *** post are the all the  rage)
> fglrx-control : Control panel for the ATI graphics accelerators
Control panel for the ATI Radeon and FireGL graphics accelerators.
This package provides the control panel comnpiled for Qt3.

xorg-driver-fglrx : Video driver for ATI graphics accelerators
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports: * ATI Radeon 8500, 9000, 9100, 9200, 9250 (R2xx) * ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx) * ATI Radeon X700, X800 (R4xx) * ATI Mobility 9000, 9600, 9800 * ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200 * ATI Mobility FireGL 9000, T2, T2e
This package provides 2D display drivers and hardware accelerated OpenGL.

xorg-driver-fglrx-dev : Video driver for ATI graphics accelerators (devel files)
Video driver for the ATI Radeon and FireGL graphics accelerators.
This package provides definitions for the GL and GLX extensions and the FGLRXGAMMA extension interface library.

and then I got this when I tried running UT again

```
three@CondorV2:~$ cd /home/three/ut2004
three@CondorV2:~/ut2004$ ./ut2004
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
three@CondorV2:~/ut2004$

```

---

### Post by audax321 on 2006-02-02
Did you activate the driver by editting xorg.conf.

After installing the packages you should have:

1. added it to /etc/modules with the following command:
echo fglrx | sudo tee -a /etc/modules

to double-check if this command worked:
cat /etc/modules  (you should see fglrx listed in the output)

2. editted xorg.conf:
[INDENT]a. Open xorg.conf in gEdit: sudo gedit /etc/X11/xorg.conf[/INDENT]
[INDENT]b. Find Section Device and look for the entry for driver, and change it from "ati" to "fglrx"[/INDENT]
[INDENT]c. Finalize the changes by rebooting the computer.[/INDENT]


If you did the above and it still doesn't work, try killing esd and then starting the game. To kill esd, just open terminal and type:
killall esd

ESD is the Enlightenment Sound Daemon and sometimes prevents the game from running on some computers.

To see if you are getting 3d acceleration, type the following command and post what kind of FPS you get:
glxgears -iacknowledgethatthistoolisnotabenchmark

---

### Post by threethirty on 2006-02-02
before I save this is this what you are talking about in #2 (sorry but I'm really working outside of my comfort zone, and dont want to ruine anything)
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
```

***EDIT: actually I'm gonna go for it, never a better time to learn then the present***

---

### Post by threethirty on 2006-02-02
IT WORKED, OMFG IT TOTALLY WORKS!!!!!!\\:D/ 

thanks for all your help\\:D/

---

