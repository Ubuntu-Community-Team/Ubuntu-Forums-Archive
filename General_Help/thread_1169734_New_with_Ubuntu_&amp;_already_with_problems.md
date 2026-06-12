---
title: "New with Ubuntu &amp; already with problems"
date: 2009-05-25
forum: General Help
---

### Post by joelop on 2009-05-25
Hi All,

I've always wanted to try Linux but never got the courage to do it. A month or so ago I found out the existence of **Wubi** so through it I managed to install Ubuntu and, until last Saturday, it's been working fine.

A week ago I bought an external USB hard-drive because my old USB hard-drive was giving problems. On Friday night I plugged in both external HD's before switching on my laptop (I read somewhere this was the safest way of doing it) and Windows XP did not load. I got the message saying something like:
[B][I]
Win did not load because there are missing or damaged files:

C\windows\system32\config\system[/I][/B]

As I was in a hurry (and I want to get rid of Win a.s.a.p.) I didn't pay too much attention to this problem and run Ubuntu instead.

The very next day I did the same thing (plug HD's first) under UBUNTU. I gave the command to copy/paste some files from HD-1 to HD-2 and went to do something else. After 30 min. I went to check how long would it take for the task to finish and found out that the laptop was not responding. The Caps Lock led and the one with a lock simbol were flashing. Both HD's weren't making noises as they do when working so I thought the OS got stuck so I had to switch it off. Now, everytime I switch it on I get the following message:[B]

ALERT! /HOST/UBUNTU/DISKS/ROOT.DISK DOES NOT EXIST. DROPPING TO A SHELL![/B]

What can I do now? Today I have no working OS whatsoever :(

---

### Post by keypox on 2009-05-25
> **joelop said:**
> Hi All,

I've always wanted to try Linux but never got the courage to do it. A month or so ago I found out the existence of **Webi** so through it I managed to install Ubuntu and, until last Saturday, it's been working fine.

A week ago I bought an external USB hard-drive because my old USB hard-drive was giving problems. On Friday night I plugged in both external HD's before switching on my laptop (I read somewhere this was the safest way of doing it) and Windows XP did not load. I got the message saying something like:
[B][I]
Win did not load because there are missing or damaged files:

C\windows\system32\config\system[/I][/B]

As I was in a hurry (and I want to get rid of Win a.s.a.p.) I didn't pay too much attention to this problem and run Ubuntu instead.

The very next day I did the same thing (plug HD's first) under UBUNTU. I gave the command to copy/paste some files from HD-1 to HD-2 and went to do something else. After 30 min. I went to check how long would it take for the task to finish and found out that the laptop was not responding. The Caps Lock led and the one with a lock simbol were flashing. Both HD's weren't making noises as they do when working so I thought the OS got stuck so I had to switch it off. Now, everytime I switch it on I get the following message:[B]

ALERT! /HOST/UBUNTU/DISKS/ROOT.DISK DOES NOT EXIST. DROPPING TO A SHELL![/B]

What can I do now? Today I have no working OS whatsoever :(

sounds like you installed via wubi.  And you deleted your windows partition?
Also maybe your drive letters changed?  Try using just the old usb drive. See what happens?  Then you can plug it in while in ubuntu.

---

### Post by joelop on 2009-05-25
> **keypox said:**
> sounds like you installed via wubi.  And you deleted your windows partition?

No, I didn't.

> **keypox said:**
> Also maybe your drive letters changed?  Try using just the old usb drive. See what happens?  Then you can plug it in while in ubuntu.

Just done it but no success; it's like it's waiting for me to type any command or something [WRITE THROUGH], but I don't know what to do.

---

### Post by gillmt on 2009-05-25
I'm not an expert but maybe you should not plug anything in to your laptop until your system has booted. A colleague of mine plugged a USB key into our work PC and we worked out that the machine was looking for an operating system on her key as the PC was set to boot from CD or USB before looking at the hard drive.

---

### Post by monton on 2009-05-25
If you are "booting" with the USB drives plugged in then your computer is trying to boot from one of them. If I boot my XP computer with a usb drive plugged in it stops and says there is no operating system - because it looks to the USB drive. No OS there!
If you were running from a USB drive then it is probably looking for the OS there.
Not a Linux problem. More a newbie problem. Frustrating but a good way to learn.
Good luck, Monton

---

### Post by joelop on 2009-05-25
> **monton said:**
> If you are "booting" with the USB drives plugged in then your computer is trying to boot from one of them. If I boot my XP computer with a usb drive plugged in it stops and says there is no operating system - because it looks to the USB drive. No OS there!
If you were running from a USB drive then it is probably looking for the OS there.
Not a Linux problem. More a newbie problem. Frustrating but a good way to learn.
Good luck, Monton

Well, isn't it through the BIOS that the systems is told to boost from a CD ROM, A: drive, C: or whatever?

How comes now that by having some USB equipment plugged in makes the system act otherwise?

---

