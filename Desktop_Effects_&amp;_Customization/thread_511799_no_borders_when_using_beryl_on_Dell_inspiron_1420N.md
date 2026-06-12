---
title: "no borders when using beryl on Dell inspiron 1420N"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by purplearcanist on 2007-07-28
On my dell inspiron 1420 (it came w/ ubuntu), there are no window borders with beryl with the beryl and compiz window managers.  Has anyone else had this problem with this computer, or does anyone know how to solve it.

Just so you know, I upgraded it to gusty gibbon, and beryl works excellent (except for no window borders).

---

### Post by Happy_Man on 2007-07-28
> **purplearcanist said:**
> On my dell inspiron 1420 (it came w/ ubuntu), there are no window borders with beryl with the beryl and compiz window managers.  Has anyone else had this problem with this computer, or does anyone know how to solve it.

Just so you know, I upgraded it to gusty gibbon, and beryl works excellent (except for no window borders).
Right-click the beryl icon in the tray, and reload everything. Make sure that the Emerald decorator is set.

---

### Post by purplearcanist on 2007-07-28
I tried that, but still no borders.

---

### Post by Happy_Man on 2007-07-28
Did you install emerald?

```
sudo apt-get install emerald emerald-themes
```

---

### Post by nick_h on 2007-07-28
Check that the following lines:

```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```

are in the device section of your /etc/X11/xorg.conf

---

### Post by purplearcanist on 2007-07-28
No, those lines aren't in xorg.conf.

---

### Post by Mornedhel on 2007-07-28
Just so you know, they aren't in mine either, and Beryl works flawlessly for me (window borders and all).

---

### Post by purplearcanist on 2007-07-28
It still doesn't work after adding in those lines.

---

### Post by nick_h on 2007-07-28
What graphics card are you using? I think the lines I gave you are only relevant for nvidia cards.

---

### Post by purplearcanist on 2007-07-28
an Intel Integrated Graphics Media Accelerator 3000

---

### Post by purplearcanist on 2007-07-29
tap, it is so annoying to have no borders

---

### Post by purplearcanist on 2007-07-30
tap tap

---

### Post by nick_h on 2007-07-30
Check that your colour depth is set to 24.

There are some threads in the *Desktop Effects* section about this.  Have a look [here](http://ubuntuforums.org/showthread.php?t=447275)  and [here](http://ubuntuforums.org/showthread.php?t=512682) for example.

---

### Post by seipherdj on 2007-07-30
Try running "beryl-manager" from a terminal .... what is the output? any errors?.... ie "no composite" or any "AIGLX".
I had the border problem when trying to run the fglrx ati driver with aiglx .... switched to the opensource driver in the kernel.
I also remember no being able to use my keyboard for anything.

make sure you have the 

Section "Extensions"
Option  "Composite" "enable"
EndSection 

and 

Section "DRI"
Mode 0666
EndSection

in your /etc/X11/xorg.conf

also on the DRI note post the output of 

glxinfo | grep dir

---

### Post by purplearcanist on 2007-07-30
Here is the output for glxinfo | grep dir:

direct rendering: Yes

The lines you mentioned were not in the xorg.conf file, so I put them there.  Now, i'll restart the computer to see if beryl works.

---

### Post by purplearcanist on 2007-07-30
Still no window borders.:(

---

### Post by purplearcanist on 2007-07-31
tap, i want this fixed

---

### Post by purplearcanist on 2007-08-01
By the way, here is the output of beryl-manager:
 **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011
beryl: decoration: property ignored because version is 20070319 and decoration plugin version is 20061011

Something looks suspicious on the last three lines.  Could those lines hold a clue to why beryl isn't working?

---

### Post by nick_h on 2007-08-02
I just did a quick search on the error message you are getting.  Have a look [here](http://ubuntuforums.org/showthread.php?p=3061776) and [here](http://ubuntuforums.org/showthread.php?p=2897958).

---

