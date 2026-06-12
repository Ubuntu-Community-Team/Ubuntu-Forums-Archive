---
title: "Is gnome 3 available in ubuntu?"
date: 2012-09-03
forum: Desktop Environments
---

### Post by temetvince on 2012-09-03
I'm thinking about making the switch to ubuntu, but I really like gnome 3. Is there an ubuntu version for gnome 3?

---

### Post by Jamie_Edwards on 2012-09-03
> **temetvince said:**
> I'm thinking about making the switch to ubuntu, but I really like gnome 3. Is there an ubuntu version for gnome 3?

Yes it is, but not by default. You have to launch the terminal and enter the following commands:

```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell
```

After it's done it's job, sign out of your session, press the cog type icon next to your name and select "Gnome" and sign in again.

You have Gnome 3 ( or Gnome Shell )

I'm actually using it myself right now :D

---

### Post by twipley on 2012-09-03
[http://www.omgubuntu.co.uk/2012/09/gnome-flavoured-ubuntu-spin-releases-alpha](http://www.omgubuntu.co.uk/2012/09/gnome-flavoured-ubuntu-spin-releases-alpha) -- on the news;

expected release date: at about the end of october;

---

### Post by temetvince on 2012-09-03
Thank you. Once I'm in gnome 3, how would I get rid of unity from taking up hard drive space? I'm using an ssd, and so every little bit of space counts.

---

### Post by MARP1961 on 2012-09-03
You need to investigate Gnome Shell Remix 12.04. It is the latest Ubuntu with Unity removed. I've been using it for three days and so far I'm very happy:
[http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

---

### Post by 73ckn797 on 2012-09-03
After installing 12.04 go to Software Center and install "Synaptic Package Manager." Once installed open it and install "gnome-session-fallback" and "gnome shell". You can also install "gnome" which will give a complete package or just "gnome-core".  Gnome shell will probably install gnome-core as a dependency.

I would also install "gdm" = Gnome Display Manager and select it when prompted for choice of display managers. I removed the "lightdm" but only after installing "gdm". If this step is not followed you will likely boot into a shell with the computer totally useless.

To remove Unity copy the following to a terminal:
```
sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel  unity-2d-spread unity-asset-pool unity-services unity-lens-files  unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common  indicator-sound indicator-power indicator-appmenu libindicator7  indicator-application evolution-indicator indicator-datetime  indicator-messages libnux-2.0-0 nux-tools 
```There will be several residual Unity pieces you can remove using Synaptic Package Manager.

I have used this method on 4 computers, 2 of them today.

Looking at the info on the remix, mentioned above, what I recommend will be the same or very close to it.

---

### Post by temetvince on 2012-09-03
Thank you all.

---

### Post by Jamie_Edwards on 2012-09-04
> **temetvince said:**
> Thank you. Once I'm in gnome 3, how would I get rid of unity from taking up hard drive space? I'm using an ssd, and so every little bit of space counts.

I never thought about removing Unity, although I don't use an SSD. But at the same time, I guess Unity serves as a backup just in case Gnome somehow breaks on mine and I have to revert back to Unity for a while XD

---

