---
title: "Compiling my own kernel"
date: 2009-03-22
forum: General Help
---

### Post by kpraytor on 2009-03-22
Good morning! I have a question concerning compiling my own kernel. I have heard about the numerous benefits that this can provide, but I think I'm in over my head. I know that there are quite a few tutorials out there about how to download the source, make necessary changes, etc., but no one really explains what all of the options are and how they affect specific computers.

Basically, I was wondering if there was some kind of guide to give me insight into what all of the options are and how they affect me and my laptop. If anyone knows what options would work best for my computer, that would be even better. But I know that's a lot to ask. Thanks again in advance to any and all help concerning this topic!

My computer:

Dell Inspiron 1501
AMD TL-56 Processor
2GB Ram
80 GB HDD (no dual boot)
Intrepid Ibex
2.6.27-11-generic (kernel version)

Any other specs that would be needed for some assistance, just let me know :)

Thanks again and I love the Ubuntu forums

---

### Post by sekinto on 2009-03-22
The [Gentoo Handbook]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7") has some good instructions on how to do this. There are some things you need to change/skip though.

You can skip setting the time zone, this should have already been set when you installed Ubuntu.

You would want to change
```
emerge gentoo-sources
```
to
```
sudo apt-get install linux-source
```

Then you should be able to follow the manual configuration steps.


I don't know if Ubuntu does anything else differently though, I would wait for someone with more expertise to come along before you follow those instructions.

---

### Post by 3Miro on 2009-03-22
[http://www.kernel.org/doc/](http://www.kernel.org/doc/)

[http://www.mjmwired.net/kernel/Documentation](http://www.mjmwired.net/kernel/Documentation)

Basically recompiling the kernel is not trivial and you should have a pretty good idea of what is going on. You can experiment of course, but you might run into troubles.

---

### Post by kpraytor on 2009-03-22
Thanks for the documentation. This should give me something to do. I have a lot of time seeing as how it is spring break this week for me. I understand that recompiling the kernel is not trivial. I am actually downloading the source files and creating a new kernel that I can choose in GRUB. I absolutely do not have the guts to edit the kernel I'm using right now. 

I will begin the long, time consuming task of reading through the provided documentation and returning to post any questions, ideas, etc.

Thanks again for the help!!!

---

### Post by kpraytor on 2009-03-22
Ok, I began reading through the documentation provided on kernels.org, and I have ran into an issue.

> 2.1.2.2 Creating a custom kernel configuration

The most common user interface for configuring the kernel is menuconfig, an interactive terminal based menuing interface invoked through the makefiles via "make menuconfig". This interface groups the configuration questions into a series of menus, showing the current values of each symbol and allowing them to be changed in any order. Each symbol has associated help text, explaining what the symbol does and where to find more information about it. This help text is [COLOR="Blue"]_also available as html_[/COLOR].

The menuconfig interface is controlled with the following keys:

    * cursor up/down - move to another symbol
    * tab - switch action between edit, help, and exit
    * enter - descend into menu (or help/exit if you hit tab first)
    * esc - exit menu (prompted to save if exiting top level menu)
    * space - change configuration symbol under cursor
    * ? - view help for this symbol
    * / - search for a symbol by name

Other configuration interfaces (functionally equivalent to menuconfig) include:

    * make config - a simple text based question and answer interface (which does not require curses support, or even a tty)
    * make xconfig - QT based graphical interface
    * make gconfig - GTK based graphical interface


I got to this section and followed the link to the help text as an html file link, when I click on it I received these options and nothing else:

    * alpha
    * arm
    * avr32
    * blackfin
    * cris
    * frv
    * h8300
    * ia64
    * m32r
    * m68k
    * m68knommu
    * mips
    * mn10300
    * parisc
    * powerpc
    * s390
    * sh
    * sparc
    * x86
    * xtensa

I assume I choose the one that applies to my computer and utilize that documentation to learn about the available options, but I think I am too much of a noob to know which one is for my computer! Any help would be greatly appreciated! Thanks!

---

### Post by RedSquirrel on 2009-03-23
x86. However, it is probably easier to read the help text for each option while you are configuring the kernel from inside the **menuconfig** interface.

---

