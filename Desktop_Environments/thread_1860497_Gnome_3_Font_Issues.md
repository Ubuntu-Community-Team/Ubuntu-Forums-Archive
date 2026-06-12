---
title: "Gnome 3 Font Issues"
date: 2011-10-14
forum: Desktop Environments
---

### Post by Lucas Ford on 2011-10-14
Hey,

I just installed Ubuntu 11.10 today, and was pretty disappointed with Unity. I installed the GNOME Shell to replace it, and everything seemed to be working alright. As soon as I entered GNOME, though, I noticed there were a few... parts... missing. Fonts all over the menus are broken, occasionally the top panel gets covered in a bright blue color, and some menus come up distorted strangely. I'd give some screenshots of it, but it only takes screenshots of my desktop, even when I have windows open. I've tried uninstalling and reinstalling a few times. Also, I have the FGLRX drivers installed, but for some reason the post-release update to the drivers refuses to install. I have a log for that if it'd help anyone. I'd really like to use GNOME 3 if possible, so any help is appreciated.

Thanks,
Sam

---

### Post by skatona on 2011-10-24
> **Lucas Ford said:**
> Hey,

I just installed Ubuntu 11.10 today, and was pretty disappointed with Unity. I installed the GNOME Shell to replace it, and everything seemed to be working alright. As soon as I entered GNOME, though, I noticed there were a few... parts... missing. Fonts all over the menus are broken, occasionally the top panel gets covered in a bright blue color, and some menus come up distorted strangely. I'd give some screenshots of it, but it only takes screenshots of my desktop, even when I have windows open. I've tried uninstalling and reinstalling a few times. Also, I have the FGLRX drivers installed, but for some reason the post-release update to the drivers refuses to install. I have a log for that if it'd help anyone. I'd really like to use GNOME 3 if possible, so any help is appreciated.

Thanks,
Sam

same problem here ..  mostly with the top panel fonts.  can't read them.

---

### Post by crdlb on 2011-10-24
That is a known issue with the fglrx driver. The default radeon driver should run GNOME Shell assuming it supports your GPU, but its performance for gaming is not as good.

---

### Post by typhoon_tip on 2011-10-24
Same here with Thinkpad T400 and fglrx proprietary driver. I have tried to revert to the stock driver which supports my Radeon HD 3400, but apart from performance, which are good enough, it keeps the GPU always over 60C, which is not good for me (I am living in the tropics, so...), while the ATI driver keep it cool at sub 50 almost all the time.

With stock driver everything works fine, both Unity and Gnome 3.

I would say to give it a shot and try Unity + ATI driver, I installed 11.9 from ATI website and performance are even better. Still have to try if they fixed Gnome 3 issues, but as far as I am concerned, with a bit of tweakes Unity looks just as good and usable as any other Desktop software.

---

### Post by typhoon_tip on 2011-10-24
NO, ATI Driver 11.9 does not fix totally Gnome 3, altough I have to say is now almost totally usable (get issues when opening the dash by the active top-left corner, and then it frozen entire computer after 2nd logon/logoff attempt).

---

### Post by Visceral Monkey on 2011-10-26
Same problem. And I can't go back apparently either. Uninstalling doesn't fix the problem. Freaking ATI. :(

---

### Post by Harry66 on 2011-11-26
I don't think it's the graphics driver or Gnome 3. I think Ubuntu just needs to get the packages up to the version that works.

If I boot up the **Fedora 15** or **16** live CD on the same PC  (ATI Radeon) the top bar colour, font and Icons are absolutely fine. And I don't think it's fallback mode, because there's the ripple when the mouse goes to the top-left corner.

In the meantime, I'm either using Gnome Classic mode or Xfce, depending on my mood ;-)

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/870569](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/870569)

---

### Post by crdlb on 2011-11-26
> **Harry66 said:**
> I don't think it's the graphics driver or Gnome 3. I think Ubuntu just needs to get the packages up to the version that works.

If I boot up the **Fedora 15** or **16** live CD on the same PC  (ATI Radeon) the top bar colour, font and Icons are absolutely fine.

Fedora, like Ubuntu, uses the open source 'radeon' driver by default.

---

### Post by Bularthip on 2011-11-27
So, is there anything we can do? I use CCC 11.11 Drivers, also fglrx drivers are installed. Still, using Gnome is annoying and hard as animations lag and stuck, flashes and even crashes the system. I have ATI Radeon HD 5770. I'd really like to use Gnome, but it seems I have to stick with the Classic Gnome.

---

