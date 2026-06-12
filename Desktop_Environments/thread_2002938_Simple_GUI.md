---
title: "Simple GUI?"
date: 2012-06-13
forum: Desktop Environments
---

### Post by Cyberpawz on 2012-06-13
I am on a laptop I call Old Man, and there is a reason, it's 12 years old, yet it can run quite well Ubuntu 12.x as long as the bells and whistles are turned off.

I have a question, is there a GUI that is minimalist, yet functional? I'm not talking server GUI minimalist, but something that I can use that still looks decent without getting overly confused where everything is. 

I was using Ubuntu originally, but I don't like how they utilized Unity... is there any GUI out there that would allow an old laptop use Ubuntu with little to no "lag"?  Yes I'm expecting some lag, but the laptop is new enough where I've made it use SATA and 802.11G networking wireless cards. So it's not your average laptop.

---

### Post by 3Miro on 2012-06-13
What you are looking for is not "GUI", but "Desktop Environment".

Unity 3D is out of the question on such an old machine and Unity 2D still comes with some effects. I wouldn't think it would work on 12 year old hardware.

For a light environment, look into LXDE or Lubuntu. You can install LXDE easily if you already have Ubuntu installed (i.e. you don't have to install lubuntu from scratch).

Another option is to use XFCE, although XFCE is heavier. Some of the Gnome 2 ports like Cinnamon and Mate may work too. There is also Gnome-classic (i.e. Gnome-fallback) that may work too.

If you want to go as light as possible, look into standalone Windows Managers, but those may be tricky to setup and they can be really lacking in options.

Here is a page that will show you how to switch between different DE:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by nothingspecial on 2012-06-13
I would use [[COLOR="Blue"]Lubuntu[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")

---

### Post by Cyberpawz on 2012-06-13
> **3Miro said:**
> What you are looking for is not "GUI", but "Desktop Environment".

Unity 3D is out of the question on such an old machine and Unity 2D still comes with some effects. I wouldn't think it would work on 12 year old hardware.

For a light environment, look into LXDE or Lubuntu. You can install LXDE easily if you already have Ubuntu installed (i.e. you don't have to install lubuntu from scratch).

Another option is to use XFCE, although XFCE is heavier. Some of the Gnome 2 ports like Cinnamon and Mate may work too. There is also Gnome-classic (i.e. Gnome-fallback) that may work too.

If you want to go as light as possible, look into standalone Windows Managers, but those may be tricky to setup and they can be really lacking in options.

Here is a page that will show you how to switch between different DE:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

I've attempted LXDE, but every time using the minimal CD, I install LXDE, it installs Lubuntu instead, and that's not what I want done.I thought Lubuntu was LXDE...am I wrong?

---

### Post by 3Miro on 2012-06-13
> **Cyberpawz said:**
> I've attempted LXDE, but every time using the minimal CD, I install LXDE, it installs Lubuntu instead, and that's not what I want done.I thought Lubuntu was LXDE...am I wrong?

Ubuntu  = Kernel + Xorg + Gnome 3 + Unity and Unity specific settings
Lubuntu = Kernel + Xorg + LXDE + LXDE specific settings

Minimal Ubuntu = Kernel (when I say Kernel, I obviously include some basic utilities like bash and apt-get)

All Ubuntu variants come with small tweaks in settings that correspond to the environment, the splash screen for example.

You can install Ubuntu and then install LXDE and then you will have both Gnome 3 + Unity and LXDE, but you will not have the LXDE specific settings. If you are making a clean install, go for Lubuntu. If you already have Ubuntu, then go ahead and just install LXDE, you may have to make small adjustments manually, but it should be less hassle than reinstalling.

If you want to go from the minimal installation up, then regardless of the environment that you want, you always have to install Xorg and some additional tools and utilities. However, LXDE is so minimal already that I don't think you will gain anything.

---

### Post by critin on 2012-06-13
> it's 12 years old, yet it can run quite well Ubuntu 12.x as long as the bells and whistles are turned off.

Here is an easy solution to return to Gnome Classic in 12.04

[http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/)

---

### Post by critin on 2012-06-13
> **Cyberpawz said:**
> I am on a laptop I call Old Man, and there is a reason, it's 12 years old, yet [COLOR=Red]**it can run quite well Ubuntu 12.x as long as the bells and whistles are turned off.**[/COLOR]

I have a question, is there a GUI that is minimalist, yet functional? I'm not talking server GUI minimalist, but [COLOR=Red]**something that I can use that still looks decent without getting overly confused where everything is. **[/COLOR]

I was using Ubuntu originally, but I don't like how they utilized Unity... is there any GUI out there that would allow an old laptop use Ubuntu with little to no "lag"?  Yes I'm expecting some lag, but the laptop is new enough where I've made it use SATA and 802.11G networking wireless cards. So it's not your average laptop.

Or if you just want an easier menu there is this.  

[http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/)

---

### Post by Cyberpawz on 2012-06-13
> **critin said:**
> Or if you just want an easier menu there is this.  

[http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/)

Is there a way to have ubuntu, just without all the fluff? I like ubuntu, but it bogs down everything with the "fancy stuff" like Unity... Can I uninstall Unity and replace it with another desktop environment?

---

### Post by black veils on 2012-06-13
the distribution Lubuntu **is** Ubuntu, but without the Unity desktop environment etc (fluff), it will have the LXDE desktop environment instead.

from your first post, LXDE (or the distribution Lubuntu) is what you want.

if you want to just install LXDE within your current Ubuntu distro, then do this ```
sudo apt-get install lubuntu-desktop
``` restart the computer after it is finished, then at the login box there is an icon, click it, and choose lubuntu.

---

### Post by oldfred on 2012-06-13
Lightweight Desktop enviroment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

Re: What is the difference between Debian, Fluxbox, XFCE, ..
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE
[]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments")

---

### Post by Cyberpawz on 2012-06-13
> **black veils said:**
> the distribution Lubuntu **is** Ubuntu, but without the Unity desktop environment etc (fluff), it will have the LXDE desktop environment instead.

from your first post, LXDE (or the distribution Lubuntu) is what you want.

if you want to just install LXDE within your current Ubuntu distro, then do this ```
sudo apt-get install lubuntu-desktop
``` restart the computer after it is finished, then at the login box there is an icon, click it, and choose lubuntu.

That is what I figured, I just wanted to make sure that's all :)

Thanks. Would it be beneficial to blow away the others so it is the only option?

---

### Post by black veils on 2012-06-13
> **Cyberpawz said:**
> That is what I figured, I just wanted to make sure that's all :)

Thanks. Would it be beneficial to blow away the others so it is the only option?


if by blow away, you mean uninstall Unity, you would be best leaving that alone. it is lighter to install the distribution Lubuntu, than to use Ubuntu with the LXDE desktop, but its ultimately your choice, whichever you prefer. i think you should try the LXDE desktop in your current Ubuntu, and see how it goes.

---

### Post by Cyberpawz on 2012-06-13
> **black veils said:**
> if by blow away, you mean uninstall Unity, you would be best leaving that alone. it is lighter to install the distribution Lubuntu, than to use Ubuntu with the LXDE desktop, but its ultimately your choice, whichever you prefer. i think you should try the LXDE desktop in your current Ubuntu, and see how it goes.

Already tried LXDE outright, I didn't like some things about it, but thanks for your help.

---

### Post by black veils on 2012-06-13
have you tried the xfce desktop? its lighter than those other desktops, but has plenty of functionality, you can configure panels, and apply panel themes/images,

```
sudo apt-get install xubuntu-desktop
```

---

### Post by afixane on 2012-06-13
If you want a very simple DE, you can try openbox.
```
sudo apt-get install openbox
```

Openbox it's a bit difficult, here, i find a complete tutorial [here]("http://urukrama.wordpress.com/openbox-guide/") !:p

---

### Post by critin on 2012-06-13
> **Cyberpawz said:**
> Is there a way to have ubuntu, just without all the fluff? I like ubuntu, but it bogs down everything with the "fancy stuff" like Unity... Can I uninstall Unity and replace it with another desktop environment?


Depends on what you mean by 'fluff'.

Did you scroll down the page of the other link; the one about Gnome Classic?  It doesn't use unity, but gives a desktop like ubuntu before all the changes.  If you wanted to keep ubuntu ( I understand from one of your posts that you **did not** want lubuntu), you **wanted ubuntu**, so going back to classic is the answer.

Users will naturally recommend their own favorites, and I do the same.  I only like ubuntu, don't like lubuntu or kubuntu,  and my machine is old so can't run unity 3d.  I use 2d on one partition and gnome classic on another.

---

### Post by Cyberpawz on 2012-06-14
I'm looking at FVWM-Crystal, any thoughts?

---

### Post by Rodney9 on 2012-06-14
> **Cyberpawz said:**
> I'm looking at FVWM-Crystal, any thoughts?

Looks as though it may not be getting updated.


Openbox is a favourite of many, on old and new pc's.

Openbox Guide

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Rodney

---

### Post by Cyberpawz on 2012-06-14
> **Rodney9 said:**
> Looks as though it may not be getting updated.


Openbox is a favourite of many, on old and new pc's.

Openbox Guide

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Rodney

Too bad, it looked nice... 

I'll look into openbox. Thanks.

---

### Post by efball3 on 2012-07-03
> **Cyberpawz said:**
> Too bad, it looked nice... 

I'll look into openbox. Thanks.

I'm using fvwm (no crystal).  It takes some configuring at first, but it's fast and it works.  Great for old machines (and new ones).

---

