---
title: "Beryl with Nvidia and Edgy Freezes.."
date: 2007-02-22
forum: Desktop Environments
---

### Post by HoMe_CaNiBaL on 2007-02-22
I there.

I have freezes with beryl last svn from trevino. i had that problem with dapper and edgy is the same thing.

My system freeze and i had to reset with button, because nothing works. Keyboard or mouse. When freezes, its when beryl is doing a animation (for example: when minimize the window, with magic lamp).

My current system:

Intel Pentium 4 2.8Ghz HT
Asus P4C800 DLX
2x 512Mb
120Gb + 160Gb Seagate IDE
Aopen Geforce 6600GT 128Mb AGP
Audigy 1

If metacity is running, i never had that problem, so, have to be beryl, BUT, without beryl, i dont have fun! My system runs up to 1month on Windows XP overclocked, and now, i reset my configuration in BIOS, to see if freezes disapear. But still there. 

Now i'm working with metacity, but i wont beryl.

Can you help me?

Thanks for your wasting time with me.

(If you dont understanding my english, i'm sorry, i'm portuguese)

---

### Post by HoMe_CaNiBaL on 2007-02-22
someone can help me?

Please?

---

### Post by kpkeerthi on 2007-02-22
Can you tell me which guide you used to install and config beryl?

---

### Post by HoMe_CaNiBaL on 2007-02-22
I there.

I used [Beryl-Project Guide](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia) and after i change to Trevino repository. Add Composite and Dri modules...

I had the same problem in dapper. Can be from motherboard? Because to install i have to do something like "linux no apic irqpoll isa_pnp_reserve=18"..

Thanks

---

### Post by kpkeerthi on 2007-02-22
Try [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and see if it makes any difference.

---

### Post by HoMe_CaNiBaL on 2007-02-23
> **kpkeerthi said:**
> Try [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and see if it makes any difference.

Still having the same problem... After a animation the computer freezes...

My computer isnt compatible? I try Compiz and never freezes, but i like Beryl...

Thanks

---

### Post by iHenry on 2007-03-01
Hi,

A similar problem here... Sometimes Ubuntu freezes using Beryl and nothing works.. :S

I reset my computer 6 times this night ... so I will stop using  Beryl.. :'(

PC:
P4,  3.1
1GB RAM
ATI Radeon 300X 256 megas,

---

### Post by tcpip4lyfe on 2007-03-12
Same problem.  Been fighting it for a couple weeks now.

---

### Post by Donnw on 2007-03-18
I had it working but for some reason it now  freezes the computer completely as soon as it loads.  :(

---

### Post by jbcola on 2007-04-07
I have the same problem with an Nvidia 6600, and even with a Nvidia 7600GT an Asus A8V Mobo.

The "NvAGP"         "1" - "3" options in the Xorg.conf helped during some weeks.. then the whole Ubuntu started hanging again....

I think it's linked to the Asus motherboard...

I'll try with the official Nvidia driver ...

---

### Post by jbcola on 2007-04-07
It seems to work flawless now, with the latest Nvidia driver : NVIDIA-Linux-x86-1.0-9755-pkg1.run
Just some effect have jitters ...

NvAGP value : 2

---

