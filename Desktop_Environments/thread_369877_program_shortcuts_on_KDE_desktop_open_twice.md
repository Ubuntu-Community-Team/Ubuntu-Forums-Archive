---
title: "program shortcuts on KDE desktop open twice"
date: 2007-02-25
forum: Desktop Environments
---

### Post by hvymtlsteve on 2007-02-25
Hello,
I was originally running Gnome but installed KDE last night because one of the main programs I would like to use seemingly requires it. 
It seems that any program shortcuts on the desktop open two instances of the program when I use them. Is there some way around this?
(If I can't fix it, I might just try putting my main programs on the main panel and not keep shortcuts on the desktop)

Steve

---

### Post by highneko on 2007-02-25
Maybe the programs open with a single click and you're double clicking? It's not likely tho. Change to your desktop directory and check if the files are linking twice maybe?
```
cd ~/Desktop
file *
```

---

### Post by hvymtlsteve on 2007-02-25
> **highneko said:**
> Maybe the programs open with a single click and you're double clicking? It's not likely tho. Change to your desktop directory and check if the files are linking twice maybe?
```
cd ~/Desktop
file *
```

Aha, that's what it was, I'm a doofus. 
I've been sheltered to Windows for most of my life, so the double click is natural to me. 
Thanks for pointing this out :D

---

### Post by highneko on 2007-02-25
Ah. It's good to see you got it working. Thanks for letting us know. n_n

If you prefer double clicking then there are ways to use double clicks instead. I'm not a kde user tho.

---

### Post by Tahir on 2007-03-03
type kcontrol in a terminal and in the application that now appears; in the left hand column, click on peripherals, then inside that, mouse.  In the general tab there is an option to change it to double click.

Happy double clicking away :)

---

### Post by ninja_in_pajamas on 2008-02-12
Um...I'm having this same issue while NOT double clicking.  Also, it happens with programs I launch from the menu, and it doesn't always happen.  I've been having this problem since 7.04.

---

### Post by Tank84 on 2008-04-24
Have the same problem!

Things to know:
1: i'm not double clicking
2: if i start the promgram as "run command" (ALT+F2) it still starts twice
3: if i start it from konsole, then it starts only once!
4: if i logout and log in as root: same problem

Anybody done or use things in the past like:
1: installed nvidea driver (for old cards) [mine is GeForce 2 MX440)?
2: installed compiz?
3: edited the /etc/sudoers file?
4: installed kbfx taskbar (eyecandy)?
5: using openSUSE 10.3
6: using 3.5.7 (release 72.6)
7: kernel: 2.6.22.17

Lets solve this dam problem, it's really going on my nerves! 

program application start load open launch twice two times

---

