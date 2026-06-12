---
title: "WoW on WINE with Berly and AIGLX"
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by H0SS on 2007-02-13
Ok, so the only way that I have been able to get Beryl to work with my ATI 9800xt was by using this script [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html) that by defaults uninstalls fglrx if installed and installs aiglx.  

Beryl works wonderfully with this driver, but after I installed wow on wine and did all tweaks I noticed that FPS were so bad it wasnt even worth playing.  So I then removed beryl and the aiglx drivers and tried to install fglrx.  After all this I was getting an error stating that it could not start 3d acceleration.  

Heres, my question.  Is it possible to play wow with the aiglx drivers?  If not, is it possible to get beryl to work with fglrx with an ATI 9800xt, and does anyone know why I am getting this error?

---

### Post by slaw_dawg on 2007-02-13
Im no expert at this, but I use beryl and aiglx with my nvidia 6800 ultra. When I am going to play wow, I simply select the gnome window manager from the beryl manager( the little diamond shape in my notification area) to turn beryl off while I play wow. And I am getting an avg 40+ fps with all settings turn on and high. 

While beryl is running, and I try to play wow, it does dramatically affect performance, but this is for any opengl application I am using. I believe the reason for this is the window manager is rendering your desktop and window, and having to render the application or game at the same time.

---

### Post by Yoooder on 2007-02-13
Running Beryl as your window manager while gaming will really put a hurt on your video card.  For the better performace you can use Metacity for your window manager, (the previous comment was right, the option to change your window manager is in beryl-manager's diamond icon).

If you want to show off your environment then this should produce satisfactory results.  When I game I want my game to have as much of my machine as possible, so I have OpenBox installed as well as GNOME, and use that for my gaming (it's bare-bones, leaving a lot smaller footprint than a full-featured wm)

---

### Post by Sammi on 2007-02-13
@HOSS
I think you're confused about how ATI drivers for Linux work.

Firstly there's nothing called a aiglx driver. Aiglx is a feature, which is built in to xorg, in order to allow accelerated indirect GLX rendering to work, which in turn make 3d applications and composition effects, like those that Compiz and Beryl provide, play nice together. You should read up on aiglx [here]("http://en.wikipedia.org/wiki/Aiglx"), to get a deeper understanding of what it is.

There is on the other hand the open source driver for ATI video cards, often referred to as the "ati" or "radeon" driver, and the closed source proprietary driver, called "fglrx". The open source driver in a part of Ubuntu, and you should be able to find it in the repositories, while you can find very good instructions on fglrx here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

