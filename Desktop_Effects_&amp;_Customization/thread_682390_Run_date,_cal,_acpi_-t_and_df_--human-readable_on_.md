---
title: "Run date, cal, acpi -t and df --human-readable on terminal open"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by pmgr33r on 2008-01-30
Hey i was just wondering if there is a way that i can run "date; cal; acpi -t; df --human-readable" upon opening the terminal? Also is there a way to get it to always open on the right side of the screen, preferably without having to use other programs such as tilda, i like the default terminal. Thanks

---

### Post by erginemr on 2008-01-30
You can make coomands run at each terminal session by adding them to your .bashrc config file in your home directory. So, open
```
sudo vim ~/.bashrc
```
and add the following line to the end of the file:
```
date; cal; acpi -t; df -h
```

For instance, an Ubuntu based distro, Linux Mint uses this technique to display a "fortune" each time the user opens up a terminal window. Unfortunately, I don't know how to write them to the right-side of the panel, if that is at all possible.

While you are on it, you may want to give a try to "conky", which is a cool system info application that will reside on your desktop:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

```
sudo aptitude install conky
```

---

### Post by pmgr33r on 2008-01-30
Thats exactly what I wanted. Thanks

---

