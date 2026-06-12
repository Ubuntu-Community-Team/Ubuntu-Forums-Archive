---
title: "How do you add color to sections of boot menu?"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by omarian on 2007-10-14
Hi.

I am trying to customize my boot menu. I am using Feisty Fawn and have figured out how to add colors to the /boot/grub/menu.lst file so that the boot menu looks a little nicer than black and white. My computer dual boots windows xp and ubuntu. What I have done is created a heading for XP and a heading for Ubuntu in ways such as:

******Windows Operating System**********
Windows XP Professional
******Linux Operating System*************
Ubuntu 2.6.x.x....
Ubuntu 2.6.x.x.... (recovery mode etc).

What I would like to do is have the lines that say Windows Operating System and Linux Operating System have their own colors. Is that possible?

This is a condensed version of my menu.lst file:

[COLOR="DarkOliveGreen"]timeout		10

# Pretty colours
color green/black black/red
highlight white

title ***********Linux Operating System***************
root

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a441edf9-399c-414a-a222-f657245c1c4b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a441edf9-399c-414a-a222-f657245c1c4b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a441edf9-399c-414a-a222-f657245c1c4b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a441edf9-399c-414a-a222-f657245c1c4b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title ************Windows Operating System************
root

title        Windows XP Professional
root        (hd0,1)
savedefault
makeactive
chainloader +1

[/COLOR]

Any ideas?

Thank you.

---

### Post by FuturePilot on 2007-10-14
I think this is what you want.:)
[http://ubuntuforums.org/showpost.php?p=2766189&postcount=40]("http://ubuntuforums.org/showpost.php?p=2766189&postcount=40")

---

### Post by omarian on 2007-10-14
Thanks FuturePilot.

I am somewhat confued by that site. This code:

splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz
foreground ffe4b5
background f4a460

assumes that you are using a splash image doesn't it? I don't have a splash image?

Can I use the last two lines after each line I want to add a color to? How is this supposed to work?

Thank you for your reply!!

---

