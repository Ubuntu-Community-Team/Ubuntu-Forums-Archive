---
title: "Help Choosing a Desktop Environment"
date: 2011-10-16
forum: Desktop Environments
---

### Post by PietreWitobi on 2011-10-16
I'm going to start by saying that the Desktop Environment in 11.10 is absolutely hideous.  It reeks of the Apple environment, which I've hated for years now.  I much prefer the Ubuntu Classic, but since that's gone I'm looking for a new one.  I've already installed the gnome-session-fallback package, but that session doesn't seem to be working properly.  I've never really dealt with desktop environments, etc. before, and I'm honestly not trying to do a whole lot with it right now, I just want my look and feel not to get in my way.

Any suggestions?

---

### Post by gsmanners on 2011-10-16
I find that Xubuntu does a really good job of getting out of the way. I've heard a lot of good things about Lubuntu, as well. Might try them both out and see which one you prefer.

---

### Post by Rodney9 on 2011-10-16
+ 1 Xubuntu 11.10 is wonderful, looks so good now, very polished and so fast, they have made it great.

---

### Post by DeMus on 2011-10-16
It's total madness that so many people are driven away from Ubuntu because of the change in GUI. I've use Ubuntu for years and can't use it anymore since it is no what I chose years ago anymore, it's not what I want and like anymore.
Now we are told to use Xubuntu or Lubuntu. (as long as you stop complaining here on the forum)
Well, I made my decision last year already and made the switch to Mint which has the decency of delivering a normal, and very great looking, interface. Ubuntu, in its top years, could not stand in Mints shadow, let alone now with this gadget interface they call Unity. Diversity would be a better name since the Ubuntu camp is split up in two, those who are gadget-freaks and those who make the right decision of leaving.

---

### Post by PietreWitobi on 2011-10-16
I'd rather not re-install entirely.  Optimally, I'd just install a less-****** session option.

---

### Post by gsmanners on 2011-10-16
You could just go to terminal and type:

```
sudo apt-get lubuntu-desktop
```

Then log out and choose Lubuntu as your session at the LightDM screen.

---

### Post by PietreWitobi on 2011-10-16
> **DeMus said:**
> I've use Ubuntu for years and can't use it anymore since it is no what I chose years ago anymore, it's not what I want and like anymore.

I've sworn by Ubuntu for years - got my whole family using it on one of our computers, but these gadgets are ridiculous.  I wouldn't mind it if I could just right click and delete all the extra crap, and set up my bars the way I want them.

I saw your recommendation, and if I have to reinstall anyway, I'll probably go for Mint.  It looks nice and clean.  Thanks for posting.

---

### Post by PietreWitobi on 2011-10-16
> **gsmanners said:**
> You could just go to terminal and type:

```
sudo apt-get lubuntu-desktop
```

Then log out and choose Lubuntu as your session at the LightDM screen.

I will try that.  While we're at it - any way to get rid of LightDM?  It has that same bubble aesthetic and I hate it too.

---

### Post by gsmanners on 2011-10-16
> **PietreWitobi said:**
> I will try that.  While we're at it - any way to get rid of LightDM?  It has that same bubble aesthetic and I hate it too.

That might be pushing it. I think I'd look for a way to theme LightDM first.

---

### Post by PietreWitobi on 2011-10-16
Actually, sudo apt-get remove lightdm worked pretty well, especially since when you install a new display manager a nice new dialog asks you which one you want to default to.

I might just write a script that asks when I boot.

---

