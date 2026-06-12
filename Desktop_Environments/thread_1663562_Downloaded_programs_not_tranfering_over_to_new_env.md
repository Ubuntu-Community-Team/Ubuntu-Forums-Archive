---
title: "Downloaded programs not tranfering over to new environment?"
date: 2011-01-09
forum: Desktop Environments
---

### Post by Red Raven on 2011-01-09
So I'm semi-new. installed Ubuntu from a live CD on two machines now and I know some terminal. I recently installed the Lubuntu environment onto Ubuntu so I could switch between the two on one of my machines (I needed it of course for the smaller footprint. THe rig has really low RAM). So I loged out of Ubuntu, choose Lubuntu, and logged back in. I looked for my programs that I had DLd, like Xchat, but they aren't there. anyone know what to do?

---

### Post by SteveDee on 2011-01-10
> **Red Raven said:**
> ....I recently installed the Lubuntu environment onto Ubuntu.....

I'm not sure I understand what you are saying (but at least this will bump your thread!)

Can you confirm that you have installed Lubuntu as a separate OS alongside Ubuntu (i.e. you select either Ubuntu or Lubuntu via the Grub menu)? If this is the case, you won't be able to run your Ubuntu apps from Lubuntu.

I'm not sure what would happen if you installed the Lubuntu packages within Ubuntu. I have the LXDE package on a machine running Ubuntu and this allows me to select either Gnome or LXDE (as a session) at the log-in screen.

If any apps are not in the menu that you are sure should be there, then go to a terminal and try running them from there.
Examples:-
For Nautilus type:-
```

gksu nautilus

```
For gEdit type:-
```

gksu gedit

```
Or you could type something like:-
```

whereis nautilus

```
...to see if it is installed

---

