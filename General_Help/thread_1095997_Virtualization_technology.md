---
title: "Virtualization technology"
date: 2009-03-14
forum: General Help
---

### Post by Lucrothe on 2009-03-14
Hello,

I've recently purchased a Dell Mini 9 and did a full Ubuntu 8.10 install on it.  I'm really loving the Linux OS on the Mini, and now I'm thinking about installing Linux on my main desktop computer.  My only concern is I have special Windows software that I need for work, so I can't totally scrap windows.  Plus a lot of games are designed for the Windows environment.  So I'm thinking about doing something along the following with desktop virtualization:

Ubuntu 8.10 as the Host OS
Windows XP Pro as a Client OS
Windows Vista Ultimate as a Client OS

I'm still a Linux noob so my questions are:

-What is a good VM client for Ubuntu 8.10
-If I toggle full screen in a Client OS of Windows would I be able to play a video game? Perhaps World of Warcraft?
-Could the Virtual Desktops in Linux be setup as a full screen client OS?
-Has anyone else done something similar, if so what was your experience like?

Thanks in advance!

---

### Post by Slim Odds on 2009-03-14
VirtualBox works great... but if your Windows games are "graphic intensive" they will probably not work well in the VM.

In that case, a dual boot is what you need.

Having said that, I use XP in a VM to do some audio processing and it works fine.

P.S. You can certainly go full screen, but the VM will not give your client full access to the graphics hardware.

---

### Post by fcuk112 on 2009-03-14
> **Lucrothe said:**
> Hello,

I've recently purchased a Dell Mini 9 and did a full Ubuntu 8.10 install on it.  I'm really loving the Linux OS on the Mini, and now I'm thinking about installing Linux on my main desktop computer.  My only concern is I have special Windows software that I need for work, so I can't totally scrap windows.  Plus a lot of games are designed for the Windows environment.  So I'm thinking about doing something along the following with desktop virtualization:

Ubuntu 8.10 as the Host OS
Windows XP Pro as a Client OS
Windows Vista Ultimate as a Client OS

I'm still a Linux noob so my questions are:

-What is a good VM client for Ubuntu 8.10
-If I toggle full screen in a Client OS of Windows would I be able to play a video game? Perhaps World of Warcraft?
-Could the Virtual Desktops in Linux be setup as a full screen client OS?
-Has anyone else done something similar, if so what was your experience like?

Thanks in advance!

- Use VirtualBox.
- You can use Wine to play WoW.
- Yes, VirtualBox supports full-screen.
- I am running Win XP within VirtualBox without any problems.  Remember to install the VM guest additions to support smooth integration.

Cheers.

---

### Post by ricardoatb on 2009-03-14
If you want to play Window games that require good 3D acceleration you'll have to have a **dual boot installation**.

Actually, I have Windows XP installed as guest in VirtualBox because I'm using Adobe Lightroom and Photoshop for photo edition.

P.S.: Check if your cpu supports **virtualization instructions ("VT-x" for Intel and "AMD-V" for AMD)**. If enabled, you'll see a big improvement in performance.

[IMG]http://farm4.static.flickr.com/3467/3353327887_cf372174f1_o.jpg[/IMG]

---

### Post by Lucrothe on 2009-03-14
Wow thanks for the great advice everyone!

I was thinking the dual boot would be the best way to go for gaming, but I just wanted to double check with some more advanced Linux users. Then I'll use a VM for my applications for work & multimedia authoring.

Thanks guys! :)

---

