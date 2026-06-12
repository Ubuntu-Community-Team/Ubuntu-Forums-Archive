---
title: "kubuntu gutsy: ccsm icons gone, only log button shows up, and no susp/hibernate"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by nine01a on 2007-10-11
Kubuntu 7.10 beta. ATi 8.40.1 proprietary. compiz-kde with xserver-xgl.

Firstly, it's not that big of a deal but for some reason, ccsm has no icons for all the settings buttons. Just a gray little dialog icon next to each option.

Can't really seem to find a reason that only "Log Off" shows up on the log-off menu but I remember this used to work for me with Ubuntu Feisty. As mentioned, I just installed xserver-xgl and it automatically uses xgl and starts compiz(-fusion).

Suspend/hibernate just creates some disk activity and then goes to a blank (black) screen, leaving the power on. I noticed that if I don't use fglrx, it works properly but no big surprise there, right? Lol.

Also, I noticed that when I first installed Kubuntu, it was using the "ati" driver, if I'm not mistaken and glxinfo said that it was a "xpress200". I looked at my backed-up /etc/X11/xorg.conf's and none of them reflect these settings and every time I try to use the system settings tool to set it to ati, X won't start and I have to revert back to some random old config. I don't play games or anything like that but I would love to have CF back and maybe my suspend/hibernate would work if I could get it back to using that "xpress200" setup.

*has a small headache but thanks you for reading this*

---

### Post by explemonk on 2007-10-12
> **nine01a said:**
> Kubuntu 7.10 beta. ATi 8.40.1 proprietary. compiz-kde with xserver-xgl.

Firstly, it's not that big of a deal but for some reason, ccsm has no icons for all the settings buttons. Just a gray little dialog icon next to each option.

This is the only question I think I know the answer to.  I had this problem until I installed a required package--I *think* it was librsvg2-2, but I'm not 100% sure.  CCSM uses SVG images for the icons.  Gnome has the package installed by default but I don't think KDE does.

If that's not the right package, I'll try and go through and find my notes on setting up Compiz Fusion with KDE.  I also did stuff like install taskbar-compiz so I could only have the windows on the current desktop show in my taskbar.

---

### Post by giobik on 2007-10-30
hello, this is the firs time I write in this forum!

I had the same problem, and instaling 
 - librsvg2-2
 - librsvg2-bin
 - librsvg2-common
the icons in ccsm reappeared!

Thanks

---

