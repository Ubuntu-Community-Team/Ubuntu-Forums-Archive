---
title: "Trouble with Wubi-Vista and Busybox error"
date: 2009-03-08
forum: General Help
---

### Post by aidan_47 on 2009-03-08
Hi everyone, i am new to linux, but am keen to get it working on my laptop.

I currently have Windows Vista (home premium) installed on my HP dv6733 (dv6000 series) and have tried using Wubi to install ubuntu onto the same partition as vista. 

I have a burnt cd with Ubuntu Intrepid Ibex, and used that CD to 'Install Ubuntu inside windows'. All seemed to go well in the installation, and i chose to reboot after installation. I was pleased to see the screen where i could choose Vista or Ubuntu, and proceeded to select ubuntu. The loading screen appeared but after it was on the screen for a few seconds, i got a screen that said:
```
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I am able to run the livecd perfectly, but still this happens.

Thankyou in advance for any advice you may be able to give me.

---

### Post by silviaichiigo on 2009-03-08
Thats funny because I just had the samething happen to. It just sits there and doesnt do anything, I don't know what to do either. Glad theres someone else like me:D

---

### Post by Monotoko on 2009-03-08
Hmm...it is going into busybox, which means for some reason it cannot start ubuntu at all and is falling back on busybox, il get back to you after iv researched a little bit :P


EDIT: Okay, do the following:

1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug"
3. reboot
4, at the command line type "cat /tmp/*.debug" <enter>
5. there should be an error in the latest few lines, post it here.

---

### Post by silviaichiigo on 2009-03-08
> **Monotoko said:**
> Hmm...it is going into busybox, which means for some reason it cannot start ubuntu at all and is falling back on busybox, il get back to you after iv researched a little bit :P


EDIT: Okay, do the following:

1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug"
3. reboot
4, at the command line type "cat /tmp/*.debug" <enter>
5. there should be an error in the latest few lines, post it here.

I don't mean to thread jack, but I tried #1 and there is nothing in c:\ubuntu\disks\boot\grub\menu.lst But I did find it in c:\ubuntu\disks\install\grub\menu.lst Is this the file you are talking about? 

I tried what you said, but I dont know even know what an error code is going to look like. After inuting the cat tmp thing, it outputted a bunch of stuff, but I couldnt tell what was an error code.

---

### Post by lawson012 on 2009-05-11
> **silviaichiigo said:**
> I don't mean to thread jack, but I tried #1 and there is nothing in c:\ubuntu\disks\boot\grub\menu.lst But I did find it in c:\ubuntu\disks\install\grub\menu.lst Is this the file you are talking about? 
 
I tried what you said, but I dont know even know what an error code is going to look like. After inuting the cat tmp thing, it outputted a bunch of stuff, but I couldnt tell what was an error code.
 
 
Silviaichiigo i have the exact same problem as you and i also couldnt find anything in that folder : /

---

