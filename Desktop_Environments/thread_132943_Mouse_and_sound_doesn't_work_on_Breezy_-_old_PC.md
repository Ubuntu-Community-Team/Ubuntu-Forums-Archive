---
title: "Mouse and sound doesn't work on Breezy - old PC"
date: 2006-02-19
forum: Desktop Environments
---

### Post by SmartWarthog on 2006-02-19
Hi,

I've just installed Ubuntu 5.10 on a friend's old PC (it's a Pentium II 400 with everything *onboard*), but the mouse (it's a serial mouse) refused to work at all and the opening sound just keeps repeating as if the system had crashed. I can, however, input normally using my keyboard.
I'm very new to Linux, but I installed it on my computer and liked so much I wanted to show it to my friends. It'd be great if someone could help me!

Thanks!

---

### Post by Teroedni on 2006-02-19
what sound card is it 

paste the output of this command

```
sudo lshw -class multimedia
```

---

### Post by rudiz on 2006-02-19
Fix it with this instruction

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf

make ur changes under Mouse.

---

### Post by SmartWarthog on 2006-02-21
Hi,

I am having some trouble here...
I have been able to get the mouse working. (thanks rudiz =)  )
And I got some info on the sound board (it's onboard on a pcchips m748 mobo with a sis chipset).

The "lshw" command however brought me the "IDE" text and then crashed entirely (I had to reset).

Now both keyboard and mouse are really strange. When I click on a menu on the top it doesn't popup (I have to drag the mouse) and the keyboard repeats the keys I press as if I were holding them (I am being really careful to type this).

Please somebody help me!!!!!!!!!

---

### Post by SmartWarthog on 2006-02-21
Just fixed it... rebooted the system and the devices went back to normal!

I still need a fix to the sound though... I would apreciatte some help. Ubuntu's sound preferences tool tells me my card is a "C-Media PCI CMI8338"...

---

### Post by tanman on 2006-02-21
I am also having a similiar problem with a older computer. It has a pentium 2 also and when I click on the speaker at the top it says that sound card not dtected or gstreamer codec not installed. I have checked in the package manger and all the codecs are installed. The sound worked when windows was on it.

---

### Post by leandro_tami on 2006-05-06
I'm having the same problem with my onboard soundcard. And I had the same problem with the mouse too but I fixed it recently.
I tried to run alsaconf but it seems it's not available. I'm clueless :(

---

