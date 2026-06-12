---
title: "Plz help me install Beep Media Player"
date: 2005-10-10
forum: Desktop Environments
---

### Post by edurm on 2005-10-10
I´m trying to install [Beep Media Player](http://www.sosdg.org/~larne/w/BMP_Homepage)


I'm doing what they say to do:


1) extract the .gz


2) 
cd bmpx-0.11.3
./configure
make
make install



an error occur: configure: error: no acceptable C compiler found in $PATH (I'm using root)


the system requirements are:


> BMP requires the following libraries and their development packages installed:

    * Glib 2.4 ([http://www.gtk.org/download/](http://www.gtk.org/download/))
    * GTK+ 2.4 ([http://www.gtk.org/download/](http://www.gtk.org/download/))
    * libglade >= 2.3.1


Do I have all this requiremens ? (default 5.04 DVD instalation)

---

### Post by 11hjpphty76lkjj on 2005-10-10
You need to install a compiler to compile the software.  Try apt-get install gcc or search in synpatic for gcc.

Aaron

---

### Post by edurm on 2005-10-10
[QUOTE=kalosaurusrex]You need to install a compiler to compile the software.  Try apt-get install gcc or search in synpatic for gcc.

Aaron[/QUOTE]



You are the man :D 


After install the GCC  (Though apt-get) the following error came out:


```
appending configuration tag "F77" to libtool
./configure: line 25875: PKG_PROG_PKG_CONFIG: command not found
checking for X... no
configure: error: Cannot find X11 headers/libraries
root@ubuntu:~/Desktop/bmpx-0.11.3#

```



what 's next step?



(thks)

---

### Post by 11hjpphty76lkjj on 2005-10-10
Hmm sorry I'm not sure.  But this issue 'seems' to be a Beep Media Player issue.  I did some googling and found this:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/6e7ddbcd89d041c9/ac6cff834805b1e6?lnk=st&q=configure:+error:+Cannot+find+%22X11+headers%2Flibraries%22&rnum=1&hl=en#ac6cff834805b1e6](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/6e7ddbcd89d041c9/ac6cff834805b1e6?lnk=st&q=configure:+error:+Cannot+find+%22X11+headers%2Flibraries%22&rnum=1&hl=en#ac6cff834805b1e6)

not sure if it will help you or not..

gl!

Aaron

---

### Post by Suzan on 2005-10-10
Why don't you install the beep-media-player from the universe packages? With Synaptic maybe? This is sooooo easy!

---

### Post by edurm on 2005-10-10
[QUOTE=Suzan]Why don't you install the beep-media-player from the universe packages? With Synaptic maybe? This is sooooo easy![/QUOTE]



I could install but it has the same xmms problem, it frezzes when I push play :confused: 



this is starting to piss me off



BTW thanks for helping

---

### Post by Wolki on 2005-10-10
[QUOTE=edurm]
After install the GCC  (Though apt-get) the following error came out:
```
appending configuration tag "F77" to libtool
./configure: line 25875: PKG_PROG_PKG_CONFIG: command not found
checking for X... no
configure: error: Cannot find X11 headers/libraries
root@ubuntu:~/Desktop/bmpx-0.11.3#

```
what 's next step?[/QUOTE]

It tells you that it needs X11 headers& libraries. library packages start with "lib", headers end with "-dev" In this case, you need libx11-6 and libx11-dev.

That's just in general, Suzan is right: It's a lot easier to just install the beep-media-player ubuntu provides. Do the "Adding Universe and Multiverse" part here: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Then, in synaptic, search for "beep-media-player", check the checkbox in front of the name, click apply, apply, wait until it's done and profit :)

---

### Post by Wolki on 2005-10-10
Ugh, double post... sorry.

[QUOTE=edurm]I could install but it has the same xmms problem, it frezzes when I push play :confused: 
[/QUOTE]

Start it, go to options/preferences, and set the audio output plugin to esd. Everything should work then.

---

### Post by Kapre on 2005-10-10
[QUOTE=edurm]I could install but it has the same xmms problem, it frezzes when I push play :confused: 



this is starting to piss me off



BTW thanks for helping[/QUOTE]

edurn - its not the problem with the apps (XMMS). You just have to change the setup of it. Go to options---then preferences and then change the  output plugin to ESD or OSD or ALSA. Then close it and restart XMMS. Even BMP when you successfully installed it needs to change the output plugin.

K

---

### Post by edurm on 2005-10-12
UFF<  Why it's so hard on Linux?

THank you, 

The key to the problem was change the plugin to ESD and than restart the program.


Now I have the best audio player out there :D

---

