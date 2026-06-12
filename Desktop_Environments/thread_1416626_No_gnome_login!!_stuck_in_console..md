---
title: "No gnome login!! stuck in console."
date: 2010-02-26
forum: Desktop Environments
---

### Post by Roig on 2010-02-26
Hello, 

I have a problem, yesterday i was installing something related to GTK library >_< to compile Freeciv game, but i think i messed up all.. 

After the library install the desktop gone crazy and i have to reset my computer.

Now i can select the kernel in grub BUT after that I don't see the login screen of gnome, I only can see the terminal Login.

I searched the Internet what to do:

One page suggest to execute:

gdm

But the output of gdm is :

/usr/sbin/gdm-binary: symbol lookup error: /usr/lib/libgio-2.0.so.0 undefined symbol: g_thread_gettime

-------------------------

another thing i tried is:

startx

But the output is:

blablabla
(WW) fglrx: No matching device section for instance (BusID PCI:0@1:0:1)found
(EE) config/hal: couldnt initialise context: unknown error (null)

waiting for X server to shut down

xauth: error in locking authority file /home/dani/.Xauthority



Well, I think that the error i have to solve is in gdm... 

But anyone can explain me how to solve it please? i don't want to reinstall :'(

Thank you!! and sorry for my english!

---

### Post by Kakers on 2010-02-26
Firstly make sure you have everything installed, as it seems like it is not picking up gnome:

```
sudo apt-get install gdm x-window-system
```then use startx, if that doesn't work you could try uninstalling them and putting them back on

```
sudo apt-get remove gdm x-window-system
sudo apt-get install gdm x-window-system
```

---

### Post by Roig on 2010-02-26
> **Kakers said:**
> Firstly make sure you have everything installed, as it seems like it is not picking up gnome:

```
sudo apt-get install gdm x-window-system
```then use startx, if that doesn't work you could try uninstalling them and putting them back on

```
sudo apt-get remove gdm x-window-system
sudo apt-get install gdm x-window-system
```


I have installed both, but i can't uninstall gdm
```

sudo apt-get remove gdm     gives me that:

gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
..
[some dkpg errors]
..

Edpkg: error processing gdm (--remove)
Errors processing:

 indicator-session
 gdm

E: Sub-process /usr/bin/dkpg returned an error code (1)

```

I think i messed up a library? or what? >_<

More tips ?

---

### Post by trimmer on 2010-02-26
To fix broken dependancies try these two things:

apt-get install -f

and

dpkg --configure -a

Once those are done you should be able to try the previous suggestions.

---

### Post by Roig on 2010-02-27
> **trimmer said:**
> To fix broken dependancies try these two things:

apt-get install -f

and

dpkg --configure -a

Once those are done you should be able to try the previous suggestions.

I have no problem with broken dependancies. Those commands did nothing :(.

The problem is that GDM is not starting because this error:

/usr/sbin/gdm-binary: symbol lookup error: /usr/lib/libgio-2.0.so.0 undefined symbol: g_thread_gettime

anyone know how to solve this ?? I'm lost.

---

### Post by Roig on 2010-03-02
bump? :(

---

### Post by PuckstopperGA on 2011-07-15
Same thing happened to me... Googling turns up nothing but this thread.

EDIT: In case anybody else stumbles in here like I did, I found a solution to my situation. I had installed glib from a tarball. Using the terminal I CD'd into the extracted tarball dir, and ran "sudo make uninstall". That solved it.

---

