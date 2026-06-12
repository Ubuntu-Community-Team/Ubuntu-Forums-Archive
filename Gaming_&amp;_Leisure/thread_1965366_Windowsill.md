---
title: "Windowsill"
date: 2012-04-25
forum: Gaming &amp; Leisure
---

### Post by jakejw93 on 2012-04-25
Hey guys hows it going? Not posted on here in AGES.

So I got the humble indie bundle today and I thought I'd try Windowsill first, there was no sound....

Wondering if anyone else is having this problem and if there is any fixes?

---

### Post by Perfect Storm on 2012-04-25
Try start the game through the terminal and see what it says.
Also try;
```
killall pulseaudio
```

Good idea to report to the devs of the game about the soundbug.

---

### Post by jakejw93 on 2012-04-25
> **Artificial Intelligence said:**
> Try start the game through the terminal and see what it says.
Also try;
```
killall pulseaudio
```

Good idea to report to the devs of the game about the soundbug.

jakeward@jakejw93:~/Downloads$ aoss ./Windosill-linux-1.0.7-1334787847 
./Windosill-linux-1.0.7-1334787847: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking

(Windosill-linux-1.0.7-1334787847:9012): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Windosill-linux-1.0.7-1334787847:9012): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(Windosill-linux-1.0.7-1334787847:9012): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


Not much I don't think? 

Also good idea, I tried killall pulseaudio but didn't help :(

---

### Post by cmont899 on 2012-04-25
The following should at least get rid of the pixmap error:

sudo apt-get install gtk2-engines-pixbuf

---

### Post by jakejw93 on 2012-04-28
> **cmont899 said:**
> The following should at least get rid of the pixmap error:

sudo apt-get install gtk2-engines-pixbuf

Thanks, this is the only error I receive now

jakeward@jakejw93:~/Desktop$ ./Windosill-linux-1.0.7-1334787847 
./Windosill-linux-1.0.7-1334787847: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking

---

### Post by forbidden404 on 2012-04-29
> **jakejw93 said:**
> Thanks, this is the only error I receive now

jakeward@jakejw93:~/Desktop$ ./Windosill-linux-1.0.7-1334787847 
./Windosill-linux-1.0.7-1334787847: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking

I found in another case that this could be a compilation error, so you should report this to the developers and wait

---

### Post by oldrocker99 on 2012-04-29
I'm running a fresh installation of Kubuntu 12.04, and I was pleased to see that Windosill ran the first time I started it. It is one fantastic litle diversion. I DID get this in the terminal:

./Windosill-linux-1.0.7-1334787847: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Windosill-linux-1.0.7-1334787847:4013): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

Still and all, it ran just dandy. I don't mind having a second copy of a game; it's all for causes I am happy to support.

---

### Post by Perfect Storm on 2012-04-29
Those errors indicate that you missing/running/requires 32-bit libs on your 64-bit machine.

---

### Post by JoeA42 on 2012-04-30
Hi im really new to ubuntu and i mean i love but im still getting around it, and well i would really like some help with the new humble bundle, i downloaded all 4 games and i dont have any idea how to run or install them, i used to be windows user, and as far as running it i did enable all the options to run as a program on the properties menu, and my computer is a 64 bit machine running ubuntu 12.04 please i would really apreciate some help

---

### Post by JoeA42 on 2012-04-30
i think i found the problem i was trying to install botanicula and i discoverd that i needed to have adobe air and then i found this post to help me do it, [http://askubuntu.com/questions/87447/how-can-i-install-adobe-air?answertab=active#tab-top](http://askubuntu.com/questions/87447/how-can-i-install-adobe-air?answertab=active#tab-top) now i mentioned before that i had a 64 bit operative system i had to install this (wich i dont know what it is and would really apreciate an explication) sudo apt-get install ia32-libs to run the 32 bit installer, then i tried to open the windosill file and it worked, so i wanted to know how it happend, i belive that the file i installed is some sort of 32 bit thingy to run 32 bit application and the reason why i could not run the file before was because i lacked of it.

---

### Post by forbidden404 on 2012-04-30
> **JoeA42 said:**
> i think i found the problem i was trying to install botanicula and i discoverd that i needed to have adobe air and then i found this post to help me do it, [http://askubuntu.com/questions/87447/how-can-i-install-adobe-air?answertab=active#tab-top](http://askubuntu.com/questions/87447/how-can-i-install-adobe-air?answertab=active#tab-top) now i mentioned before that i had a 64 bit operative system i had to install this (wich i dont know what it is and would really apreciate an explication) sudo apt-get install ia32-libs to run the 32 bit installer, then i tried to open the windosill file and it worked, so i wanted to know how it happend, i belive that the file i installed is some sort of 32 bit thingy to run 32 bit application and the reason why i could not run the file before was because i lacked of it.

When your system is 64 bit, you have only the 64 libs, some sort of programs just work in 32bit, so when you run sudo apt-get install ia32-libs, you're installing in your pc the 32 libs, making that programs work.

---

### Post by rare HERO on 2012-05-01
> **JoeA42 said:**
> Hi im really new to ubuntu and i mean i love but im still getting around it, and well i would really like some help with the new humble bundle, i downloaded all 4 games and i dont have any idea how to run or install them, i used to be windows user, and as far as running it i did enable all the options to run as a program on the properties menu, and my computer is a 64 bit machine running ubuntu 12.04 please i would really apreciate some help

I also don't know where to start. I downloaded the file: 
Windosill-linux-1.0.7-1334787847
and, have no idea what to do next.

---

### Post by prana on 2012-05-02
> **rare HERO said:**
> I also don't know where to start. I downloaded the file: 
Windosill-linux-1.0.7-1334787847
and, have no idea what to do next.

This is a flash based game and is 32 bit so if you have flash installed on the 32 bit version of Ubuntu it should be as simple as making the file executable and then running it from the command line.

In order to do that, using the terminal, go to the directory where you downloaded Windosill and execute the following commands:

```
$ chmod +x Windosill-linux-1.0.7-1334787847
```

Press Enter and then

```
$ ./Windosill-linux-1.0.7-1334787847
```

Then press enter. The game should open in a window.

---

