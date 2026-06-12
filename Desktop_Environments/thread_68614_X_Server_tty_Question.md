---
title: "X Server tty Question"
date: 2005-09-23
forum: Desktop Environments
---

### Post by xtacocorex on 2005-09-23
This may be the wrong part of the forum, but I'm going to give it a shot anyway. 
Kubuntu is my first look at a Debian based distro, since I came over from Fedora. 

I run Hoary on my laptop and decided that I don't need 6 virtual terminals since it uses up extra power, so I commented out tty2-6 on my /etc/inittab file. 

I know that X wants to use tty7, but I'd like it to use tty2 since that is now open. I searched around trying to figure out what file contains the command to start X on tty7, but I couldn't find it.

Is this even possible and if it is, where is the file at that I need to change?

Thanks in advance for any help.

---

### Post by mlomker on 2005-09-23
I've never tried to do that, but what makes you think that it uses extra power?

---

### Post by xtacocorex on 2005-09-24
From my point of view, the extra virtual terminals are using up processor power, by getting rid of the processes, it frees up voltage going into the processor which could in turn save from draining the battery.

I'm not a Computer Engineer, but that's how it seems to me. 

As for changing the X tty, it'd be more for convenience.

---

### Post by mlomker on 2005-09-24
You'd change the following lines in /etc/kde3/kdm/kdmrc:

```

ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
ServerVTs=-7

```

The corresponding line for gnome is in /etc/gdm/gdm.conf:

```

FirstVT=7

```

---

### Post by xtacocorex on 2005-09-24
Worked Perfectly! Thanks for the help.

---

