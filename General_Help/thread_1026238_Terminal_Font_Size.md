---
title: "Terminal Font Size"
date: 2008-12-30
forum: General Help
---

### Post by sdibias on 2008-12-30
Whenever I drop into a terminal (ctrl+alt+f1) I'm very annoyed that the font size is so HUGE, does anyone know how to change this? 

I'm using 8.10 Intrepid...

---

### Post by sdibias on 2008-12-30
bump = anyone?

---

### Post by dagnabit dang doohickey on 2008-12-30
Edit /boot/grub/menu.lst to change the resolution.

Find the defoptions section of menu.lst:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```
Add [vga=791]("http://damnsmalllinux.org/wiki/index.php/Vga%3Dxxx") at the end of the defoptions:
```
# defoptions=quiet splash vga=791
```
Update grub:
```
sudo update-grub
```
Reboot.

---

### Post by sdibias on 2008-12-30
Thank you that did it, however it introduced another issue. Now when I boot up the Ubuntu splash screen that used to be small and centered is bigger and on the right, any ideas on why this happened?

---

### Post by dagnabit dang doohickey on 2008-12-30
I don't use a splash, so I can only guess that the splash resolution is 640x480.

You may need to edit /etc/usplash.conf for a 1024x768 resolution and possibly run *dpkg-reconfigure usplash*.

Maybe someone more familiar with this can advise.

---

### Post by cdtech on 2008-12-31
Just for information, here are the codes for the vga-statement:
```
       640x480	800x600	1024x768  1280x1024
8 bpp	  769	 771	 773	  775
16 bpp	 785	 788	 791	  794
32 bpp	 786	 789	 792	  795
```

---

### Post by sdibias on 2008-12-31
So how did changing that entry to 791 change my Ubuntu boot up splash screen if these are setup in two different text files?

:confused:

---

### Post by dagnabit dang doohickey on 2008-12-31
Editing menu.lst didn't change the splash.

Adding vga=xxx to menu.lst changed the console resolution, but it seems usplash is set to use a 640x480 resolution. So, the trick is to set usplash to use the new resolution.

I don't have a /etc/usplash.conf file. Can you post yours?

---

### Post by sdibias on 2008-12-31
Looks like it's set to my notebooks resolution

```

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1400
yres=1050

```

Once I made the change on the to menu.lst this happened :(

---

### Post by dagnabit dang doohickey on 2008-12-31
The following is copied directly from [this page]("https://help.ubuntu.com/community/ConsoleFramebuffer").

Set usplash resolution
```
# Usplash configuration file
xres=1024
yres=768

```
Rebuild the kernel image
```
sudo update-initramfs -u

```
Reboot

---

### Post by Slim Odds on 2008-12-31
edit the file /etc/default/console-setup

look for FONTFACE and FONTSIZE

No need to rebuild anything or reboot :(

---

### Post by sdibias on 2008-12-31
Ok forget usplash how can I turn this off?

---

### Post by neur0 on 2008-12-31
When without X, the easiest way to set the console font properties is
```
sudo dpkg-reconfigure console-setup
```

at least on Ubuntu server, but it should be available on all other *buntu variants.
(basically does some things already described, but in a curses menu fashion without manually editing config files)

---

### Post by sdibias on 2008-12-31
I just removed the word, "splash" from the line that starts with
#defoptions= in the /boot/grub/menu.lst followed by "sudo update-grub"

Hope that works!

---

### Post by sdibias on 2008-12-31
> **neur0 said:**
> When without X, the easiest way to set the console font properties is
```
sudo dpkg-reconfigure console-setup
```

at least on Ubuntu server, but it should be available on all other *buntu variants.
(basically does some things already described, but in a curses menu fashion without manually editing config files)

What exactly am I supposed to change in here? The only thing I need is small fonts because by default there are way too big

---

### Post by Slim Odds on 2008-12-31
> **sdibias said:**
> What exactly am I supposed to change in here? The only thing I need is small fonts because by default there are way too big

Maybe the fonts?

How far did you get? The font selection comes near the end.

---

### Post by sdibias on 2008-12-31
> **Slim Odds said:**
> Maybe the fonts?

The fonts yes I get that thanks however I would rather just edit settings in a text file and not run through some menu driven setup tool

---

### Post by Slim Odds on 2008-12-31
> **sdibias said:**
> The fonts yes I get that thanks however I would rather just edit settings in a text file and not run through some menu driven setup tool

Did you read my previous post?

edit /etc/default/console-setup

```
sudo vi /etc/default/console-setup
```

look for FONTFACE and FONTSIZE

---

### Post by ajcham on 2008-12-31
> **Slim Odds said:**
> Did you read my previous post?

edit /etc/default/console-setup

```
sudo vi /etc/default/console-setup
```

look for FONTFACE and FONTSIZE

On my system at least (I assume it is default) the console-setup file is read-only (444), so you'll need to do: ```
sudo chmod 644 /etc/default/console-setup
```

---

### Post by Slim Odds on 2008-12-31
> **ajcham said:**
> On my system at least (I assume it is default) the console-setup file is read-only (444), so you'll need to do: ```
sudo chmod 644 /etc/default/console-setup
```

in vi, if you use```
:w!
``` it doesn't matter if it's read-only or not (since you're using sudo you have the power).

You don't really want to leave that file writable.

---

### Post by sdibias on 2008-12-31
> **Slim Odds said:**
> Did you read my previous post?

edit /etc/default/console-setup

```
sudo vi /etc/default/console-setup
```

look for FONTFACE and FONTSIZE

I did and I meant to respond because right now it shows

FONTFACE="Fixed"
FONTSIZE="16"

I changed the FONTSIZE to 8 and then 13 but I didn't see any difference, what are yours set to ?

---

### Post by Slim Odds on 2009-01-02
> **sdibias said:**
> I did and I meant to respond because right now it shows

FONTFACE="Fixed"
FONTSIZE="16"

I changed the FONTSIZE to 8 and then 13 but I didn't see any difference, what are yours set to ?

Mine is:
FONTFACE="VGA"
FONTSIZE="8"

I'm not sure that 8 will work with "Fixed".

---

### Post by theozzlives on 2009-01-02
wouldn't this all be easier using Startup Manager?

---

### Post by Slim Odds on 2009-01-02
> **theozzlives said:**
> wouldn't this all be easier using Startup Manager?

Modifying /etc/default/console-setup also configures the terminals that are accessed via Ctrl-Alt-F[1-6]

The original post was not asking about startup.

---

### Post by kiisu on 2009-01-02
I don't understand how this all got so complicated.

I did this the other day:

in terminal, right-click -> edit current profile -> appearances tab -> change the slider that controls the font size.

---

### Post by ajcham on 2009-01-02
> **kiisu said:**
> I don't understand how this all got so complicated.

I did this the other day:

in terminal, right-click -> edit current profile -> appearances tab -> change the slider that controls the font size.

The OP asked about the actual terminal (that is the one accessed by Ctrl+Alt+[F1…F6]) rather than the Terminal application in GNOME.

---

### Post by Slim Odds on 2009-01-02
> **ajcham said:**
> The OP asked about the actual terminal (that is the one accessed by Ctrl+Alt+[F1…F6]) rather than the Terminal application in GNOME.

Exactly......

So many times people hear (read) what they want to hear (read).

---

