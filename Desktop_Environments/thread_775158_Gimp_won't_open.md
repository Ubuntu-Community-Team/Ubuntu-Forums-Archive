---
title: "Gimp won't open"
date: 2008-04-29
forum: Desktop Environments
---

### Post by damonjablons on 2008-04-29
For some reason whenever I try to open GIMP i get the busy mouse, but then nothing opens.

It's also missing from the System Monitor.

I tried marking it for reinstallation via synaptic, but that didn't fix anything.

Any ideas?

Thanks in advance!

---

### Post by scragar on 2008-04-29
open a terminal and type```
gimp
```paste output back here.

---

### Post by damonjablons on 2008-04-29
```

/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:5102): LibGimpBase-WARNING **: gimp: wire_read(): error

```

it actually opened when i did that though...

---

### Post by scragar on 2008-04-29
reinstall the print plugin for gimp to get rid of that little error then:
```
sudo apt-get install --reinstall gimp-gutenprint
```
then edit the menu option by right clicking the menu(the Application/Places/System buttons) and choosing edit menu, go to graphics, right click gimp and change the launcher to just read ```
gimp
```no need to specify a version or the %U, since you only have the latest version and the %U is irrelevant in this instance.

you wanna post output back from ```
gnome-system-monitor
```see if we can work out why system monitor isn't working for you.

---

### Post by revmacd on 2008-04-29
Well, I guess it's true that if you look to see if someone else asked the question then it might have already been answered. It seems to be the case with every question I have however. I just fixed my GIMP thanks to this one.

I've been a member for a couple of weeks and just figured I should say something sometime. You guy work really hard helping folks with these little issues that pop up. This forum has helped tremendously. TY

---

