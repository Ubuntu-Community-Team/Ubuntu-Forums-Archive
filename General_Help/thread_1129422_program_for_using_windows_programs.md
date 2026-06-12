---
title: "program for using windows programs?"
date: 2009-04-18
forum: General Help
---

### Post by JakeHinojosa on 2009-04-18
i think i heard of something like that. is there actually something where i can open like a game for windows, by using a program in ubuntu. and i dont want to use dual boot to do that.

---

### Post by Alterax on 2009-04-18
That would be WINE. (Wine Is Not an Emulator).  It can run many programs, so that is one option you could try.  Look at the winehq website for more information; you may be lucky enough that your game is listed among them.

And don't forget to contact the developers of your game and tell them that you would really appreciate it if they had a native Linux-compatible build.  They will be more likely to make them if they perceive a demand.

---

### Post by 73ckn797 on 2009-04-18
Running Windows from Virtual Box is another option. You can have the complete Windows OS from within Ubuntu. You can find it in Synaptic Package Manager.

---

### Post by Chemical Imbalance on 2009-04-18
In terminal:
```
sudo aptitude install wine
```

Check for compatibility with Windows programs: 
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by hikaricore on 2009-04-18
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by kdroxx on 2009-04-18
> **73ckn797 said:**
> Running Windows from Virtual Box is another option. You can have the complete Windows OS from within Ubuntu. You can find it in Synaptic Package Manager.

That's interesting . . so is it like running Ubuntu on Windows with the VM thing ??
Don't mind my terminology, I'm new to Linux.

---

### Post by 73ckn797 on 2009-04-18
> **kdroxx said:**
> That's interesting . . so is it like running Ubuntu on Windows with the VM thing ??
Don't mind my terminology, I'm new to Linux.

It IS a virtual system using Virtualbox in Ubuntu. You install Windows into Virtualbox.

---

### Post by kdroxx on 2009-04-20
> **73ckn797 said:**
> It IS a virtual system using Virtualbox in Ubuntu. You install Windows into Virtualbox.
So I'll have to boot into Ubuntu first & then run the virtual system ??

---

### Post by Volt9000 on 2009-04-20
> **kdroxx said:**
> So I'll have to boot into Ubuntu first & then run the virtual system ??

That's correct. You run Ubuntu then start up VirtualBox, which is your virtual machine. Inside that you install and run Windows. Because it's an emulated machine, Windows won't know the difference.

---

### Post by Johnny19734 on 2009-04-20
> **Volt9000 said:**
> That's correct. You run Ubuntu then start up VirtualBox, which is your virtual machine. Inside that you install and run Windows. Because it's an emulated machine, Windows won't know the difference.

Wine is okay glitchy though. Virtual Box has 3D capabilities. You can enable them. Check my Thread out to find out how :

[http://ubuntuforums.org/showthread.php?t=1110099](http://ubuntuforums.org/showthread.php?t=1110099)

You dont have to download the Beta you now can go to VirtualBox.com and download Version 2.2. let me know how the games run. I havent run Windows as a guest on a Ubuntu host. I wonder how the DX9 to Open GL perform. Let me know....

---

### Post by andrew.46 on 2009-04-20
Hi kdroxx,

> **kdroxx said:**
> That's interesting . . so is it like running Ubuntu on Windows with the VM thing ??
Don't mind my terminology, I'm new to Linux.

I attach a screenshot of my own VM of XP just so you can get an idea :-). It is a very, very cool way of doing it but make sure you have enough disk space and ram. And I would strongly recommend reading more than a few posts of the [Ubuntu Forums Virtualization section]("http://ubuntuforums.org/forumdisplay.php?f=308") before launching into it, in particular the 'stickies' written by Bhodi-zazen.

Andrew

---

### Post by Johnny19734 on 2009-04-20
Andrew - 

Do you have the latest Virtual Box Installed 2.2? I wanted to know how the 3-D  games run on it. It would be interesting to see the results....

---

### Post by andrew.46 on 2009-04-20
Hi Johnny19734,

> **Johnny19734 said:**
> 
Do you have the latest Virtual Box Installed 2.2? I wanted to know how the 3-D  games run on it. It would be interesting to see the results....

Unfortunately I am running 2.1.4_OSE and not only that I don't have any 3D games. And to tell the truth I had not realised that a new version was out so thanks for the heads-up :-).

Andrew

---

