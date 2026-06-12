---
title: "Direct Rendering NO - help!!!"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by kystorms on 2007-10-22
I had.... the desktop customizations... right from upgrade, lost and then i put this into my terminal

and go this response, i have no idea what this means, any help so i can get my 3D back?

lisac@lisac-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

lisac@lisac-desktop:~$ glxinfo|grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
lisac@lisac-desktop:~$ 


thank you
:confused:
i thought i should add that my graphics card is a ATI Radeon QY 100/7000VE

---

### Post by jimerickso on 2007-10-22
if you are using the fglrx driver with xgl direct rendering will not work, you will have to wait for the new fglrx driver.

---

### Post by kystorms on 2007-10-22
okay, can you tell me how i would find out what i am using as pertains to your comments?

how do i find out if i am uising xgl direct rendering and fglrx driver?

all i know is, i had this all working fine, could not get a cube today, followed a how to here, somewhere, lost that, changed something in my xorg, and now i am broke.
i have  no idea how to back track what i did...

thank you for any help, i just know it was all working great the day i upgraded
and i do not want to redo my entire drive to upgrade again

:confused:

---

### Post by jimerickso on 2007-10-22
first try this:

sudo apt-get install xserver-xgl

then go to system > administration > restricted drivers manager and enable driver

then restart your x session by pressing "ctrl-alt-backspace"

then log back in and tell me what happens. hope that helps!

---

### Post by BLTicklemonster on 2007-11-30
I didn't get anything in the resticted drivers after installing that, and got locked out of X (I'm finding all kinds of new ways to cirucumvent the failsafe features lately), and had to bring up a failsafe terminal and remove what I'd just installed.

Isn't there just some section of xorg.conf that you can edit to make compiz work?

---

### Post by infra_red_dude on 2007-11-30
ATI radeon 7000 WON'T work with fglrx driver. You need to use the opensource driver "ati" or "radeon" in you xorg.conf file.

---

