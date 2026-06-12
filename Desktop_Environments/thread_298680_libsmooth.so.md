---
title: "libsmooth.so"
date: 2006-11-13
forum: Desktop Environments
---

### Post by Cuppa-Chino on 2006-11-13
Hi, 
when I try and run programs such as BOINC or gqcam (user installations I guess) I keep getting this error:

```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

```

The resulting GTK window is actually anything but smooth! ;) 

I have located libsmooth.so here:
```
:~$ locate libsmooth.so
/usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so

```

I have search and found this bug report: [[launchpad 6786]("https://launchpad.net/distros/ubuntu/+source/xmms/+bug/6786") as I have an Nvidia card I thought it might apply to me

but when I try and use the fix it described there (which I decided togive a spin for the heck of it...

rm /usr/lib/tls/libGL* 
```
sudo rm /usr/lib/tls/libGL* 
Password:
rm: cannot remove `/usr/lib/tls/libGL*': No such file or directory
:~$ 

```

locating libGL* did not help me either:
```
:~$ locate libGL
/usr/lib/xorg/modules/extensions/libGLcore.so
/usr/lib/libGL.so.1
/usr/lib/libGLEW.so.1.3
/usr/lib/libGLEW.so.1.3.4
/usr/lib/libGLU.so.1
/usr/lib/libGLU.so.1.3.060501
/usr/lib/nvidia/libGL.so.1.xlibmesa
/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/usr/lib/libGLcore.so.1
/usr/lib/libGL.so.1.0.8776
/usr/lib/libGLcore.so.1.0.8776

```

Please give me a clue on what to do

---

### Post by Cuppa-Chino on 2006-11-21
bump bump

---

### Post by Cuppa-Chino on 2006-11-24
mini bump 


any help out there

---

### Post by Cuppa-Chino on 2006-12-15
bump please help - *ugly looking fonts are ruining my life well not quite but you get my drift*

---

### Post by Cuppa-Chino on 2007-01-08
Hello does noboday have this problem? Can nobody help .....

It also affects audacity for instance.

---

### Post by deadlydeathcone on 2007-01-08
> **Cuppa-Chino said:**
> Hi, 
when I try and run programs such as BOINC or gqcam (user installations I guess) I keep getting this error:

```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

```

The resulting GTK window is actually anything but smooth! ;) 

I have located libsmooth.so here:
```
:~$ locate libsmooth.so
/usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so

```

The problem is that libsmooth.so isn't in the path that the programs search for modules, so it isn't used and screws up the fonts (gqcam using GTK 1.x may have something to do with it as well). What you need to do is either export the variable GTK_PATH or possibly module_path before the apps are run and point them to the correct directory, or failing that create a symlink  to libsmooth.so where the program expects to find it. You may try placing them in /usr/lib/gtk-2.0/modules or just /usr/lib and seeing if that works; you may have to search through the documentation or source code to see for sure.

edit: Creating the folder /usr/lib/gtk-2.0/2.8.0 and symlinking to libsmooth from there should do the trick.

---

### Post by Cuppa-Chino on 2007-01-11
thanks for you help tried that from above with the link

*edit: Creating the folder /usr/lib/gtk-2.0/2.8.0 and symlinking to libsmooth from there should do the trick.*

```
sudo mkdir 2.8.0
cd 2.8.0
sudo ln /usr/lib/gtk-2.0/2.10.0/engine/libsmooth.so

sudo mkdir engine
sudo ln /usr/lib/gtk-2.0/2.10.0/engine/libsmooth.so

```

both did not help, would really like some more assistance this is still very annoying

---

### Post by Cuppa-Chino on 2007-01-22
help anybody outthere know the answer

---

### Post by Cuppa-Chino on 2007-01-31
bump

---

### Post by dr_psikick on 2007-02-02
same problem...

---

### Post by Cuppa-Chino on 2007-03-12
problem still there still no help...

any ideas this is what it looks like ... see attachment

---

### Post by Ali_ix on 2007-04-18
I have the same problem with no luck to solve yet. :(

I cant use any gtk1.x application :(

---

