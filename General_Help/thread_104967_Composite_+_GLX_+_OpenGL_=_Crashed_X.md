---
title: "Composite + GLX + OpenGL = Crashed X"
date: 2005-12-17
forum: General Help
---

### Post by Gurgeh on 2005-12-17
Can tell me how to stop OpenGL from crashing X while using composite manager. I'm enjoying the pretiness but whenever I play Quake or do something that uses OpenGL I find myself very quickly back to the login screen. Composite also hangs the system when trying to logoff, total crash just hangs, well weird...

I'm using the Synaptic GLX drivers for my BFG Nvidia 5700FX. I've written a few scripts to manage bringing composite up and down but would appreciate not having to use them.

Lovin this ubuntu thing tho, just scrapped windows and am steadily convincing my housemate to convert ;)

AMD 2800XP, nForce 2 Chipset, Nvidia 5700FX 256Mb, 768Mb RAM, 200Gb HD (Runs like dream :))

---

### Post by shakin on 2005-12-17
To allow OpenGL games with composite you need to add the following line to your xorg.conf file.
```

Option          "AllowGLXWithComposite" "true" 

```

---

### Post by Gurgeh on 2005-12-17
Done that one matey (it crashs X if I set it to "false"!) But yeah, no joy...

---

### Post by MartinG on 2005-12-17
Using the latest drivers (8174) from NVidia (not available via synaptic) helped me -- but installing is not straightforward!  If you want to try this, search the forums for others' experience.

---

### Post by Gurgeh on 2005-12-17
Hey nice to meet a fellow brit, i'm Jim from brum. I remember giving that a shot but had a gcc compiler error. Its not urgent anyways. Gonna try and back this box up before I do anything. Got it running sweet now and I wouldn't want anything to.... well, i'm not even gonna say it lol.

I know about the export CC=/etc/blah blah thingie (however it goes) but nvidia doesn't seem to support compilation with anything that didn't compile the kernel, bizarre. Pain in the arse that gcc...

---

### Post by mo_x on 2005-12-17
I think the kernel doesn't accept modules compiled with another compiler.

---

### Post by Gurgeh on 2005-12-17
Well yeah thats what I meant, r u having problems with this yourself mo_x?

---

### Post by MartinG on 2005-12-18
This thread might help:

[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)

---

### Post by Gurgeh on 2005-12-18
Hmmm, I gotta remove all the old kernels anyways at some point, just installed the k7 one - cheers for that MartinG - do the nvidia website drivers give better performance?

---

### Post by snellgrove on 2005-12-18
> Composite also hangs the system when trying to logoff, total crash just hangs, well weird...

I find if i press enter it logs off, or whatever the last option I used was :) its not crashed, you just cant 'see' the log off / shutdown screen.

what you need, is a toggle for composite, mate :) 

turn composite off, just before you fire up a game, or go to log-off etc etc - it works around all these little problems.

Theres a guide, in the main composite thread but i'll post here, what I did too.

I find when I kill the gnome-panel, it takes out something vital (dunno what) but I get an error from "bonobo activation server" and basically it screws up properly, have to log out / ctrl+alt+backspace)

so I modified a script that was in that thread, to the following:

```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xcompmgr -CcfF
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
fi

```

put that code in a file: /usr/bin/toggle_xcompmgr.bash 
chmod +x  that file, so you can run it fine (i think thats what you do) 
then create a launcher to this on your panel somewhere, or on the desktop :) 

running that launcher, will turn the composite on or off, it works wonderfully I find without killing gnome panel, which causes me major grief!! 

if you need anymore help, i pretty much followed this guide: [http://ubuntuforums.org/showthread.php?t=75527&highlight=drop+shadow](http://ubuntuforums.org/showthread.php?t=75527&highlight=drop+shadow) - only thing I modified in that script was taking out the killing of gnome-panel

---

### Post by mo_x on 2005-12-18
[QUOTE=Gurgeh]Well yeah thats what I meant, r u having problems with this yourself mo_x?[/QUOTE]
No problems here, but I am not using composite :D 
I am running the latest 1.0-8174 driver and composite gave some artifacts (on KDE) like parts of a window that are not shown, so I turned it off.

Here is a short howto for installing the latest nvidia driver.
- Install compiler etc. and linux headers.
```
apt-get install build-essential
apt-get install linux-headers-`uname -r`
apt-get instal gcc-3.4

```- Remove all packages related to nvidia driver with --purge option
```
sudo dpkg --purge nvidia-glx
sudo dpkg --purge nvidia-kernel-common
sudo dpkg --purge linux-restricted-modules-`uname -r`

```- Run the installer script (you may need a different version).
```
export CC=/usr/bin/gcc-3.4
sudo sh NVIDIA-Linux-x86_64-1.0-8174-pkg2.run

```

---

### Post by MartinG on 2005-12-18
[QUOTE=Gurgeh]Hmmm, I gotta remove all the old kernels anyways at some point, just installed the k7 one - cheers for that MartinG - do the nvidia website drivers give better performance?[/QUOTE]
I'm not a games player, so I can't comment on that, but with the distro drivers I just could not use composite.  After about ten minutes the system froze solid so I had to do a hard reset (sounds like windoze, doesn't it!).  With the new drivers I have it running all the time, with no noticeable effect on speed and really very solid.

Of course, it depends on your card, some say. Mine's a GeForce4 MX4000, so with something else your success may vary.  But I love composite, it was well worth the hassle of getting the new drivers to work.

BTW neat little howto, mo-x.  Thanks.

---

### Post by Gurgeh on 2005-12-18
Corr blimey, was expecting one reply instead I get: A howto on how to install the Nvidia drivers, some code for a much needed composite toggle button and some informative reading :) fantastic lads. Mo_x, MartinG and Snellgrove i am feeling the luuuuv and composite is beautiful isn't it, its funny when it silently crashes and ur instincts tell u there something wrong, u look about the sceen and notice the lack of shadows lol.

EDIT: Furthermore, thats a fantastic way to get the linux-headers which was what stumped me before when I tried to install the drivers. Thanks again.

---

### Post by Gurgeh on 2005-12-20
Right then, bit of an update. Got the Nvidi drivers working (still got a crashing composite problem) but the drivers work beatifully and the composite toggle works even better. Well worth the post, cheers again...

---

