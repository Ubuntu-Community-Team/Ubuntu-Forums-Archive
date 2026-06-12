---
title: "Problem enabling desktop effects"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by varunbhatbm on 2008-04-06
Hi,
I have Intel mother board with intel graphics. I mother board is 6 months old and I have 4GB RAM. When I enable desktop effects, I get error message saying desktop effects can not be enabled.
Please tell me a solution for this.

---

### Post by oligray on 2008-04-06
have you installed your graphics driver...

because i get the same message and im finding it impossible to inbstall my (VIA Chrome9) driver

---

### Post by V_max on 2008-04-06
i have the same problem!

i can't enable desktop effects!
i have a HP NX9105 laptop with GeForce4 420 Go 32M, 
512MB DDR...
driver is installed and running fine (played warsow a few times)
NVIDIA Driver Version:1.0-9

I just want to try it :D

Thx in advance!

---

### Post by sirfonners on 2008-04-06
this might help [http://taninorulez.wordpress.com/2007/10/19/the-composite-extension-is-not-available-ubuntu-gusty-gibbon/]("http://taninorulez.wordpress.com/2007/10/19/the-composite-extension-is-not-available-ubuntu-gusty-gibbon/")

its in italian but the commands are all the same
use google translate if its really buggin you

---

### Post by V_max on 2008-04-07
ok i followed the instructions (one by one) and now i have a new option in my visual effects bar...
but the only thing i can do is open preferences but i cant enable it!
i still get the : Desktop effects could not be enabled!

this is what i get when i try to run compiz from terminal:
---------------------------------------------------------
vanjo@striker:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0176 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
--------------------------------------------------------------

Any help?

---

### Post by mrmiserable on 2008-04-07
v_max

your problem relates to the memory on your graphics card (compiz requires 64meg)

possible solution is to

gksudo /usr/bin/compiz (line 44 states memory for nvidia change to 32)

now the problem maybe compiz will run
A really slow
B crash your system
C ok

hope it is c and dont blame me if it all ggoes pear shaped

also after you get compiz there maybe these problems (but lets get compiz going first)

[http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762)

[http://humani.st/ubuntu-nvidia-compiz-black-window-bug-fix/](http://humani.st/ubuntu-nvidia-compiz-black-window-bug-fix/)

good luck

---

### Post by V_max on 2008-04-08
well...i came home 2night and started my laptop-my desktop acted wierd!
icons were disapearing and all kinds fo wierd/unstable GUI stuff...
so i removed all the stuff i installed yesterday-reseted the x-org with 
nvidia-xconfig
reseted the x-server (ctrl+alt+background)
and now everithing works fine!

I think ill give compiz a rest for now :D
eheh

Thank you ALL once again!

Vanja

---

