---
title: "Boot Agent Lilo"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Xyus on 2006-07-13
Hi guys,

I'm totally new to Ubuntu (today I searched the whole day how to install my Asus Wifi Card) and I can't boot in Ubuntu anymore :confused: 

I installed win XP on my primary disk and ubuntu is on a partition on my secondary disk so I want to install a boot agent, Lilo.
I've downloaded it but I can't find a good guide how to install lilo? 

so could anyone help me out?
anyway, 
Greetings Xyus!

---

### Post by Ramses de Norre on 2006-07-13
Is there a particular reason why you want lilo? Because grub is much easier to use.. I never used lilo but I can explain you how to install grub if you want. And if I understand you correct you now just boot in windows immediately?

---

### Post by Xyus on 2006-07-13
Indeed I immediately go to windows,

When my windows was messed up (before I installed it again) I got Grub error 17 ? :confused: 

And yes please explain me how to install Grub :)

Many thanks in advance,
Xyus

---

### Post by Ramses de Norre on 2006-07-13
Pop in a ubuntu live disc and run ```
sudo grub
``` 
tell it which partition it's menu.lst file is on then tell it to install itself on the MBR. Grub counts from 0 so numbers are one less than normal. It also uses numbers instead of letters so for example /dev/hda5 is (hd0,4) to grub. /dev/hda3 is (hd0,2) and /dev/hdb7 is (hd1,6). So if your Ubuntu is on /dev/hda4 issue the commands
```
sudo grub
root (hd0,3)
setup (hd0)
quit
```
Grub should be installed then, run sudo update grub if your menu.lst file isn't correct.

---

### Post by Xyus on 2006-07-13
Ok! but one small prob, didn't get a live cd..
But I'll find it, thanks allot!

xyus

---

### Post by Ramses de Norre on 2006-07-13
The desktop cd is a live disc I think, otherwise you can download it.

---

### Post by Xyus on 2006-07-13
Yes, I just saw it, I just wanted to edit my post ](*,) 

thx alot dude!

xyus

---

### Post by Xyus on 2006-07-13
hmm :( 

I did all the steps and even took a print screen! hah
but I don't understand what you mean with updating menu.lst :confused: and what do you mean with MBR?

btw I'm also dutch so you could pm it me in dutch if it's easier for you? 
here's the screenie anyway what I took from ubuntu live:

[[IMG]http://img301.imageshack.us/img301/5779/screenshot0gm.th.png[/IMG]](http://img301.imageshack.us/my.php?image=screenshot0gm.png)

I think my bios settings are messed up because before my CMOS reset I did get a boot screen? and I really don't know what settings I got to use for boot screen.

anyway thanks alot!

xyus

---

### Post by Ramses de Norre on 2006-07-13
You need to give in the commands after "grub>" and one by one, so do sudo grub and wait untill you see that prompt and enter each line I gave you and enter in between them.

And what did you change in your bios? You mean the grub menu with "boot screen"? Only thing necesary to get that is your bios booting from the harddisk grub is installed to (so if grub is installed to the second disc you need to set the boot sequence of your bios to that).

---

### Post by Xyus on 2006-07-13
Ok I'll do that :)

and do I get a clear message if Grub is installed properly?
So The harddisk with ubuntu installed on it must be the master in boot priority? 

anyway Thanks so much!
I'm going to shut pc down and change IDE cables a bit ;p
xyus

---

### Post by Ramses de Norre on 2006-07-13
Remember to change jumpers too when you change IDE cables! I've forgotten that so many times already..
And yes, you should see some messages about setting up the menu.lst with kernel version and such but no errors, and you'll get the normal terminal back after quit.

---

### Post by Xyus on 2006-07-13
yay grub is working :) thx guys,

but Just when you thought is was working fine it isn't :rolleyes: 

when I press on "windows loader" I get an error 13 or error 15 (can't remember wich one) and it says something about invalid blabla :eek: 

so I changed my hard drive boot priority so my windows boots up first. :( 

xyus

---

### Post by Ramses de Norre on 2006-07-13
Did you change the ide drives? If so you'll need to edit /boot/grub/menu.lst to change the device windows is on. It's at the end of the file.

---

### Post by Xyus on 2006-07-13
ah thx :) 

god you're good ^^ :D

xyus

---

