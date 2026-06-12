---
title: "Nvidia video card problem on dell gx260"
date: 2009-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by macdell on 2009-08-19
I have a dell gx260, i'm trying to install an nvidia PCI card, the choices in the bios are auto or onboard (No disable) to choose which card to use. With "onboard" ubuntu works fine, but when i choose "auto" ubuntu hangs when using the pci nvidia card. I have preinstalled the recommended nvidia driver, run  several "xserver-xorg" commands (which just seems to bang on about the keyboard), sudo nvidia-xconfig just doesn't work. I believe it could be because i cannot disable the onboard card properly which is causing the hanging so i am now at your mercy...any ideas? As you can probably guess i'm new to ubuntu so any advice would be appreciated.. 
 
PS: I have the latest bios A09

---

### Post by realzippy on 2009-08-19
..all I found is:
GX260, GX270, GX280 -
Just adding an AGP video card will automatically disable the onboard video card...

If you install the nvidiadriver with your onboard card
xorg cannot find your AGP card..
Did you try to set bios to "auto",then plugin your videocard and start
the ubuntu LiveCD?

---

### Post by macdell on 2009-08-19
Thanks for the quick reply, As I said its a PCI card not AGP sadly, which is why I think i'm having this problem. I'm not sure if the bios will auto close the onboard card if its  a PCI video card. I have set the bios to auto but of course this is when it hangs on the ubuntu GUI boot screen.  Livecd? Do you mean the installation disk? and boot to it? not sure what you mean (sorry)

---

### Post by realzippy on 2009-08-19
"Livecd? Do you mean the installation disk? and boot to it?"


yep.(without installation)


If you installed ubuntu using your onboard graphics,the xorg.conf leads to your onboard graphics.If you then
plug your PCIcard,ubuntu will not find it,even when the bios should have disabled the onboard graphics and enabled the PCI card...

---

### Post by macdell on 2009-08-21
thanks for the advice, but no joy, I even tried loading with the livecd even in "safe graphics mode" (when using nvidia card and the bios set to auto just hangs). I would like to point out that this nvidia card was fine with windows so its not card or pc fault, I installed ubuntu 9.4 streight after using windows xp. I was going to try installing the latest nvidia drivers myself only to discover another problem with the console "ctrl alt f1" I just get large text and no login but this is with the onboard video card (Now it becoming a nightmare) its seems you cant do much without the console. This pc I know is not grand but it worked well with windows (which I don't want) so its getting a bit tough. I have search for solutions on all these probs with no joy, so if you have any more advice i'd be greatful. Once again thanks for you time!

---

### Post by gradinaruvasile on 2009-08-21
What model of nvidia card do u have? It is PCI or PCIexpress?

---

### Post by macdell on 2009-08-21
Hi, Its a geforce fx 5200 pci

---

### Post by gradinaruvasile on 2009-08-22
What drivers have u installed? On the Nvidia site this is the latest driver for ur card:
[http://www.nvidia.com/object/linux_display_ia32_173.14.20.html](http://www.nvidia.com/object/linux_display_ia32_173.14.20.html)

---

