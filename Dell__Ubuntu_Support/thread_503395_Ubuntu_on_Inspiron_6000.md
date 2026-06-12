---
title: "Ubuntu on Inspiron 6000"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by oudisos on 2007-07-17
Hello,

I posted these questions on the ubuntu user's mailing list before I knew about the ubuntu on Dell forum. If you've read it there I apologize, but I am hoping maybe this forum will have the answers. Anyway, here are my issues.

I have had Feisty running on a Dell inspiron 6000 laptop for about 6 weeks now. I have managed to solve most of the problems I encountered by tinkering around and or googling stuff, but there are two problems that I was unable to solve.

1- The computer comes with the intel 950 graphic accelerator. For whatever reason, I am not able to change the video memory from the 8MB it defaults to. I am running the latest (A09) bios. In the documentation, the laptop is supposed to allow up to 128 of shared video memory. Since the bios doesn't allow that, I assume the OS is what's meant to control it. Any ideas on how I can change that.

2- The sound works most of the time, but a few applications report hw:0 is already in use. (jack, audacity ..) and this can only be fixed by a reboot. Is there anyway I can find what's using hw:0. When the problem occurs I close all other applications and still get the same error message.

Thank you for any help,
Oudisos.

---

### Post by MyNameUhBorat on 2007-07-22
I'm having a similar problem with my sound. I have a Soundblaster Audigy 2 ZS and have it connected to my Logitech THX 5.1 speaker system. But when I'm on the go I the laptops own speakers don't work at all. I use to be able to just switch over to the Intel ICH6 via sound preferences but it doesn't work when I do that ever since I upgraded to Feisty a few days ago.

---

### Post by wyss84 on 2007-07-22
For the video share memory, I called Dell asked about this issue when I was using this laptop with Windows, the technician said that the amount of shared memory used will be configured automatically.  That means, full 128MB will ONLY be used when your application/OS really needs this much of graphic memory.

What will happen under Ubuntu?  Sorry, I don't know about this question.  You may try to call Dell to ask about this.  Or maybe Ubuntu does the same thing like Windows did...

---

### Post by brettr on 2007-07-23
I am just curious on how you found out how much memory your video card is using. Anyways there is a directive that you can put in your ```
/etc/X11/xorg.conf
```file.

```
Section "Device"
        Identifier      "Intel 945GM Express (Default)"
        Driver          "i810"
        BusID           "PCI:0:2:0"
       ** VideoRam        131072**
EndSection

```

Notice the VideoRam 131072 directive the 131072 is 128MB i think. I don't remember where is found the values but i am sure with a little googlilng you can find them.

---

