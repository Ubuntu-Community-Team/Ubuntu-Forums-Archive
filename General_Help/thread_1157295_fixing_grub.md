---
title: "fixing grub"
date: 2009-05-12
forum: General Help
---

### Post by bolter40k on 2009-05-12
i have two hardisks.  A 20gb and a 60gb.  I had ubuntu 9.04 installed on the secondary drive and windows on the primary.  Because windows sucks and it failed i had to reinstall it and now i cant choose to boot to ubuntu.  Now i have to reinstall grub but i do not know how.  If anyone can please help id greatly appreciate it.

---

### Post by uupreti on 2009-05-12
First Boot the Desktop/Live CD. Then go to terminal and type following

1. # **sudo grub**
2. # **find /grub/stage1**
3. grub> **root (hdX,Y)** [FONT=monospace](X, Y will be replaced by number you get from command 2.
4.[/FONT]grub> **setup (hd0)**

---

### Post by bolter40k on 2009-05-12
i already tried that id didnt work 

when i do root (hdX,Y) i get error 17 device cannot be mounted

---

### Post by uupreti on 2009-05-12
> **bolter40k said:**
> i already tried that id didnt work 

when i do root (hdX,Y) i get error 17 device cannot be mounted


Can you give output of all steps that I mentioned?? As you have multiple hard disk, you may have to use different numeric character.

---

### Post by bolter40k on 2009-05-12
ok thank you i got it fixed i was typing

sudo grub
> root (hd1,0) which was where ubuntu was installed
> setup (hd1) when it should have been 0 to overwirte MBR 

thank you for the help

---

### Post by bolter40k on 2009-05-12
solved

---

### Post by uupreti on 2009-05-12
> **bolter40k said:**
> i already tried that id didnt work 

when i do root (hdX,Y) i get error 17 device cannot be mounted

> **bolter40k said:**
> solved


You are welcome....

---

