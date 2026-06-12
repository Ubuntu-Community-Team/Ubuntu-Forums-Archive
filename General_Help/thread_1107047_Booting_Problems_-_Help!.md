---
title: "Booting Problems - Help!"
date: 2009-03-26
forum: General Help
---

### Post by bboywicked on 2009-03-26
Hello,

So this is my second topic here at the forums and this time it's a question related to booting. So I've had Windows XP before and I installed Ubuntu as dual boot from the desktop. Right now my Ubuntu OS is working fine and all I have installed everything I need so far. But here comes my question. How can I make Ubuntu the primary boot instead of Windows XP everytime I start my computer. 

At the moment, when start the computer I have 2 options to choose from. Either Microsoft Windows XP or Ubuntu. The XP is set primary so if I don't choose anything it goes straight to windows. I'd have to choose Ubuntu to go to that, obviously.

Yesterday, I tried changing the **default number** from **0** to **1** in the **boot/grub/menu.lst** but when I did that and restarted the computer and tried to get to Ubuntu, it gave me all type of errors and couldn't get inside. So I had to go back on XP and navigate to the menu.lst files and change it back to **0** from **1**. When I did that everything is back to normal, however I still have to choose Ubuntu at start so I can get into it. 

Is there anyway I can fix this? So I don't always have to choose Ubuntu to into it. I want it to make it primary and my Windows XP secondary. 

I hope I made some things clear, looking forward to some replies. 

Thanks in advance. :)

---

### Post by Sidewinder1 on 2009-03-26
The following is a copy of my menu.lst, which defaults to ubuntu. Your drive configurations may be different and you maybe using a different version, but it should get you on the right track.
HTH,
Side

## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b910a1ca-23d8-4e1a-9a18-ca6fb3527cf3 ro quiet splash locale=en_US
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b910a1ca-23d8-4e1a-9a18-ca6fb3527cf3 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.22-16-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-16-generic root=UUID=b910a1ca-23d8-4e1a-9a18-ca6fb3527cf3 ro quiet splash locale=en_US
initrd        /boot/initrd.img-2.6.22-16-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.22-16-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-16-generic root=UUID=b910a1ca-23d8-4e1a-9a18-ca6fb3527cf3 ro single
initrd        /boot/initrd.img-2.6.22-16-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by bboywicked on 2009-03-26
Hello,

Thanks for the reply. Just looked over it. Though, something ticking my brain. I'm on Ubuntu 8.10 and your menu.lst seem to have 8.04 plastered everywhere. Would it make a big difference?

Thanks,
BboyWicked

---

### Post by Dngrsone on 2009-03-26
It should work the same-- no major upgrades to grub that I am aware of between 8.04 and 8.10.

---

