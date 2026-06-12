---
title: "How Do I Play games through Wine"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by gwoodard on 2007-07-01
Can anyone give me step by step instructions on how to use wine properly? (I have SimTheme Park and CNC the First Decade installed and would like to play them:mad:)

---

### Post by cogadh on 2007-07-01
If you already installed them through Wine, then there should be an Applications menu entry for them that you can use to launch them. Beyond that, it is generally the same as using the game in Windows. It should be noted that not all games work through Wine, since it is still beta software and not all Windows API functions are working fully.

---

### Post by gwoodard on 2007-07-01
I looked for the Folder "Wine" or some other that wasn't default but could not find one

---

### Post by Enverex on 2007-07-01
> **gwoodard said:**
> Can anyone give me step by step instructions on how to use wine properly? (I have SimTheme Park and CNC the First Decade installed and would like to play them:mad:)

You say "installed" but did you actually install them in Wine or are you referring to having installed them in Windows?

---

### Post by Sammi on 2007-07-01
Here's a nice general guide on using Wine in Ubuntu: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by almkglor on 2007-07-02
I noticed that the applications menu doesn't update when new Wine applications are installed.

Try logging out, then logging in again.

---

### Post by hikaricore on 2007-07-02
Thread renamed with less confusing title.

---

### Post by gwoodard on 2007-07-02
> **Enverex said:**
> You say "installed" but did you actually install them in Wine or are you referring to having installed them in Windows?

I have installed through wine but I also dual boot with windows XP... I have only got Red Alert to run  but the keyboard does not work when I play (ex. none of the keys respond but work okay after I shut down the game)

---

### Post by Enverex on 2007-07-03
Did you turn off "Allow window manager to control created Windows" in winecfg? That's the #1 cause of that issue.

---

### Post by gwoodard on 2007-07-03
Thanks I will try that, if it doesn't work then something else is wrong (hopefully not)

---

### Post by gwoodard on 2007-07-05
Tried it, still did not work... but for another game; Worms 2, how would you install that. (for some reason when I put in the disk, it asks if to extract files or listen to audio {songs})

---

### Post by cogadh on 2007-07-05
Worms 2, a game I actually have. Here's how I got it installed:

1. Insert CD, when prompted to choose how to access it, you should have an option for "Browse Files", choose that
2. open a terminal and run this:
```
cd /media/cdrom0
```
3. The run this:
```
wine SETUP.EXE
```
4. Click on the install button and select the default options. I did choose the 22KHz sound samples and did a "Typical Installation"
5. After the install is complete, run this in the terminal:
```
cd $HOME/.wine/drive_c/MicroProse/Worms2/
```
and then:
```
wine frontend.exe
```

Have fun playing!

---

### Post by gwoodard on 2007-07-05
Sweet... Thanks!

---

### Post by Sammi on 2007-07-06
You should check out this page, if you would like to see how other games and applications work in Wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)

You can also find a lot of instructions there on getting programs working, if they need a little hacking and tweaking in order to get going.

---

