---
title: "Grub?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Isoss on 2006-06-08
I just need to understand some stuff! at the dual boot, I get following:

```

Ubuntu, Kernel 2.6.15-23-386
Ubuntu, Kernel 2.6.15-23-386 (recovery mode)
Ubuntu, Kernel 2.6.12-10-386
Ubuntu, Kernel 2.6.12-10-386 (recovery mode)
Ubuntu, Kernel 2.6.12-9-386
Ubuntu, Kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest86+
Other Operating Systems
Microsoft Windows XP Professional
--------------------------------------------
Use (up arrow) and (down arrow) keys to select which entry is highlighted.
Press enter to boot to select OS, 'e' to edit the commands before booting, or 'c' for a command-line

```

Ok, now when I first installed ubuntu, I got only
Ubuntu Kernel 2.6.12-9-386
Ubuntu Kernel 2.6.12-9-386 (recovery mode)

I dunno where the other "OSs" came from! I noticed that when I go to the first it starts loading as Kubuntu which I have installed with Gnome as a desktop, "I guess the 'Ubuntu Kernel 2.6.15-23-386' appeared after installing Kubuntu-desktop" ... 
Anyway I have the following questions:
1. What are these exactly and what is the difference between each?
2. What does 2.6.12-9-386 refere to?
3. I am new to linux, so bear this stupid question, but, what is Kernel?
4. What does hitting 'e' enable me to do exactly?
5. What does hitting 'c' enable me to do exactly?

Thanks in advance.

---

### Post by murph2481 on 2006-06-08
They are all the same OS they are just different kernals.  When you update your kernal it updates grub to pickup all the kernals you have on your machine

Kernal is like the main code that linux is based on

What i would do is boot into linux and edit your menu.list file in grub.  Go to terminal and type

cd /boot
cd grub
ls
sudo gedit menu.list

I mention the ls command so you can see all the files there i think its named menu.list (menu.lst i am drawing a blank now)  Then you can just delete the extra entries so all you have is the 2.6.15-23-386 kernal

Do not worry about hitting c or e at booting just pick the OS and press enter

---

### Post by Isoss on 2006-06-08
thanx a lot, I am not worried about hitting c or e, but just would like to know what is the function of each.

---

