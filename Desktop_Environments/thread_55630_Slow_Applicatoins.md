---
title: "Slow Applicatoins"
date: 2005-08-09
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-09
Is it normal when small applications like KBounce and about every program there in the X takes about a good 4 seconds to start? It is MUCH slower than windows.

I have a 2.66 GHZ celeron with 512mb of ram.

edit: Also, after about a half and hour, Ubuntu just freezes and you can't do a Ctrl-Alt-Backspace, or switch virtual consoles. You just have to flip the power switch. 
This bad stability is getting on my nerves. I am going to switch to Windows again if it never works right. Anyone else have this problem? Anyone know how to fix it?

---

### Post by Juergen on 2005-08-09
If you use Gnome and start a KDE-app all those KDE-libraries that are already in memory if you'd run KDE have to be loaded. 
This takes time of course

You should check if your HDs are running on DMA. In an xterm try:
```
dmesg | grep -i dma
```You should see lines for hda and/or other HDs you have.

You might also want to try [prelinking](http://ubuntuforums.org/archive/index.php/t-1971.html)
This HOWTO should still work with Hoary

---

### Post by tmasboa on 2005-08-09
dmesg | grep -i dma

does nothing. But i see what you mean with the KDE libarys

---

### Post by Juergen on 2005-08-09
> dmesg | grep -i dma
does nothing.IMHO it should. What about
```
sudo hdparm /dev/hda
```? (replace hda if you use other devices. You might have to install 'hdparm' first)

---

