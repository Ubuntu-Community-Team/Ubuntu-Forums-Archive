---
title: "CS-GO GFX went Kaput on new UBUNTU 17.04"
date: 2017-04-16
forum: Gaming &amp; Leisure
---

### Post by Sunil_Daswani on 2017-04-16
HI UBUNTU, i am a CS-GO player and since the ubuntu update to 17.04 my  screen went black... i think it must be the graphics drivers.... any  help?
pls send me the codes. i have a Dell Inspiron 15  - 3000 DUnoo  If it has NVIDIA oR INTEL Graphics... please help (i dont know how to  check..)

The computer works well, only the game doesnt work...

heres some scr shots:

[https://ibb.co/nMrK35](https://ibb.co/nMrK35)
[https://ibb.co/c3oz35](https://ibb.co/c3oz35)
[https://ibb.co/nMrK35](https://ibb.co/nMrK35)

help... i wanna play!!

---

### Post by Perfect Storm on 2017-04-16
to check your card:
```
lspci | grep VGA
```

If nvidia - Try upgrade the nvidia driver:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```

From System Settings or directly from the menu / Dash, open Software & Updates, click on the "Additional Drivers" tab, select the driver you want to use, and click "Apply changes"
The latest should be 378.13

Then reboot.

---

### Post by Sunil_Daswani on 2017-04-17
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)


^^ its intel, do same or different?

GOt to here: [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3)

but don't understand after ./configure (which works) , [U]make and make install don't work.... 
sunil@tux:~/Desktop/intel-gpu-tools-1.18$ make
make: *** No targets specified and no makefile found.  Stop.
sunil@tux:~/Desktop/intel-gpu-tools-1.18$ make install
make: *** No rule to make target 'install'.  Stop.
sunil@tux:~/Desktop/intel-gpu-tools-1.18$ 



[/U]

---

### Post by xblitz2 on 2017-04-26
I also have the same problem,  with intel HD:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)

```

---

### Post by Perfect Storm on 2017-04-26
Moved to Game forum. There may be some people who know the answer with intel and games.

---

### Post by xblitz2 on 2017-04-27
this seems to fix the problem for me:
```
[COLOR=#000000][FONT=&quot]sudo apt-get install libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386[/FONT][/COLOR]
```

---

