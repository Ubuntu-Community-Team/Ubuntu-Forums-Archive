---
title: "Official Nvidia drivers"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by noxlord on 2005-04-17
Installing the Nvidia binaries requires me to init  runlevel 3. However, it is impossible to use the common "init 3" command. How do I achieve this ?

---

### Post by Firetech on 2005-04-17
Hmm, if it's the message that tells you taht you probably got an xserver running, just login to a tty console (Ctrl+Alt+F1) and type "sudo /etc/init.d/gdm stop" (or kdm if you run kubuntu). Then run the nvidia installer and wait for it to finish. After that, to start X again, run "sudo /etc/init.d/gdm start" (or kdm if you still run kubuntu :D)

---

### Post by noxlord on 2005-04-17
when typing "gmd stop" the consol say: Gdm already running: stopping.  :neutral:

---

### Post by noxlord on 2005-04-18
ok, I got the xserveur down !!! now I need to fetch the kernel-source for the driver to compile... I looked in the apt prepositories and found no kernel sources... is this normal ?

---

### Post by brickbat on 2005-04-18
Hi, this may be a stupid question but I thought the official nvidia drivers were in the universe/multiverse repositories.  I just did an apt-get and there they were.

Here are the full instructions I followed.

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

ciao
bb

---

### Post by jdodson on 2005-04-18
yeah i would recommend installing the nvidia/ati drivers that come in ubuntu.

i created a guide that might help:
[http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

---

### Post by wolovids on 2005-04-18
Just be aware of this [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183). 

It's a nasty one!

---

### Post by jdodson on 2005-04-18
[QUOTE=wolovids]Just be aware of this [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183). 

It's a nasty one![/QUOTE]


i will, though i have never had that problem.

---

### Post by almarag on 2005-04-19
My unnoficial guide to install nvidia-drivers from [www.nvidia.com](www.nvidia.com)

1. Download the nvidia drivers from nvidia.com
2. Install the kernel headers from your kernel:

    # sudo apt-get install linux-headers-2.6.10-5-386

3. Create a symbolic link in /usr/src:

    # sudo ln -s /usr/src/linux-headers-2.6.10-5-386 linux

4. Execute the nvidia-installer:

    # sudo ./NVIDIA-installer-bla.bla.bin

5. Follow the on-screen instructions.
6. Change the appropiate lines in xorg.conf (or XFree86-4.conf if you are still using Xfree)
    
    # Load "glx"  (put the # as commentary)
    # Load  "dri"  (idem)
    Driver  "nvidia"  (instead of nv)

7. Load the nvidia kernel module:

    # sudo modprobe nvidia

8. Check if the installer add an entry in /etc/modules. If not, add the nvidia to file.
9. Restart the X server
10. Eat some cookies :)

almarag.

---

### Post by Firetech on 2005-04-25
[QUOTE=almarag]
    # Load "glx"  (put the # as commentary)
[/QUOTE]
Why would you comment out GLX? nVidia's guide sais that you should make sure that you have it on. It is correct to comment out "dri", but AFAIK, GLX is for the 3D acceleration. Without it, you may not get any 3D. I may be wrong though...
If not commenting out glx prevents X from starting, something is wrong.

---

### Post by c_dog on 2005-04-25
Why bother going through all the trouble now of installing the Nividia driver modules via scripts and whatnot. The latest Nvidia proprietory driver, 1.0.7174, has been on the Hoary CDs, DVD, and in the restricted repositories since the day (literally "the day") of Hoary's offical release. The bug mentioned earlier does not effect 7174. If you use the debs you won't have to recompile the driver module everytime the kernel gets updated.

---

### Post by Domhnull on 2005-04-26
Thanks for this tip - I used it yesterday when I switched to Linux.  I just wanted to add that you still need to edit your X config file.  

```
sudo gedit /etc/X11/xorg.conf
```

Then change

```
Driver "nv" (or Driver "vesa") to Driver "nvidia"
```

In the module section make sure you have

```
Load "glx"
```

and remove (if they exist)

```
Load "dri"
Load "GLcore"
```

Then restart X.  I just took that from the Nvidia instructions on their site for the drivers.  Anyway it worked fine for me and I was able to install Point2Play and World of WarCraft.

---

