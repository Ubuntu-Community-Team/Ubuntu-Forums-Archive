---
title: "Xubuntu 12.04 (Xfce 4.12) How to make a file launcher in top panel?"
date: 2013-01-12
forum: Desktop Environments
---

### Post by mikodo on 2013-01-12
I have done a lot of searching, but only find directions/guides/wikis on how to add apps to a launcher to the top panel.  I figured out how to add a xcalib script to be run in terminal when the launcher icon is clicked, so I am thinking somehow files should be able to be opened in one too. In gnome2, I could just drag the file to the top panel. Not so, with Xfce.

The first file, a .pdf file, is this one in my home:

```
/home/mikodo/BP.pdf
```Can anyone tell me how to do this or provide a link on how to do it? I am stuck. If it involve writing scripts, I am screwed, so kindly don't waste your time with that.

Thanks.

;p

---

### Post by Merrattic on 2013-01-12
Just create a new launcher and use the program name in the command box, along with the file you wish to open e.g.
```
evince my.pdf
```

When adding to a launcher remember to seek out the "add a new empty item" icon

---

### Post by Bucky Ball on 2013-01-12
Right click the desktop, 'Create Launcher'. Fill in appropriate details as described. Drop it on the taskbar when finished.

---

### Post by mikodo on 2013-01-12
OK guys! Thank you very much. Evince. OK, now I know the app that opens .pdf's.

I can't get to Xubuntu 12.04 right now, I am downloading some stuff, from Ubuntu 10.04 that is on the same disk. I'll following your advice, as soon as I can.

;p

---

### Post by brainwash on 2013-01-13
Simply use **exo-open** (Xfce-specific) or **xdg-open** (desktop-independent) to open a file or URL with the preferred application.
```
exo-open /home/mikodo/BP.pdf
```

---

### Post by mikodo on 2013-01-13
Thanks, for the help everyone.

I used exo-open and it works. Nice! 

```
exo-open /home/mikodo/BP.pdf
```[http://manpages.ubuntu.com/manpages/jaunty/man1/exo-open.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/exo-open.1.html)

 ```
exo-open --help

```I'll also play around with evince too!

```
man evince
```[https://help.ubuntu.com/community/Evince](https://help.ubuntu.com/community/Evince)



;p

---

### Post by mikodo on 2013-01-13
> **brainwash said:**
> Simply use **exo-open** (Xfce-specific) or **xdg-open** (desktop-independent) to open a file or URL with the preferred application.

Works for me with = .pdf, & .odt. Haven't tried .rtf . As above URL's too. According to the exo-open --help page, commands in terminal can be run. (eg.   xcalib -i -a).

Cool!

---

