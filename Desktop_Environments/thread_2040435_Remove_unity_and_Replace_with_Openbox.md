---
title: "Remove unity and Replace with Openbox"
date: 2012-08-11
forum: Desktop Environments
---

### Post by c0rnfed on 2012-08-11
Hi,
Im still fairly new to linux
im currently using dreamstudio, which has unity as its dm and i believe the wm and fm are metacity and nautilus
i want to completely remove all of this and replace it with just openbox as the wm, and thunar.
basically i want it to look more like a crunchbang setup
I tried google, and didnt come up with anything solid
please help me ubuntu community

Thanks

---

### Post by MG&amp;TL on 2012-08-11
Okay, did you actually try unity? Many people find it horrible for a couple of hours, then start to like it.

If so, here's some commands to do that, I'm not going to waste time explaining how to do it from the GUI, but it should be fairly self-explanatory:

```

#Install the openbox session
sudo apt-get install openbox
#Install thunar
sudo apt-get install thunar

```

Then select the openbox session icon from the login screen by clicking the ubuntu logo on the left of your name, then set the default FM to thunar.

---

### Post by c0rnfed on 2012-08-11
i already installed openbox and thunar

i want to use these because its not as taxing on my ram as unity is
how do i set my default fm to thunar?
and also how do i remove unity, metacity nautilus?

---

### Post by MG&amp;TL on 2012-08-12
> **c0rnfed said:**
> i already installed openbox and thunar

i want to use these because its not as taxing on my ram as unity is
how do i set my default fm to thunar?
and also how do i remove unity, metacity nautilus?

Okay. It kinda sounds like you might want to try Xubuntu or Lubuntu...they come preinstalled with lighter stuff.

I believe there's an option, I think in the 'Details' window, to set the Default FM. 

There's no real reason to, but:

```
sudo apt-get remove unity metacity nautilus
```

Be CAREFUL what this removes-if you don't know what it does, give it a google before saying 'yes'.

---

### Post by ads52 on 2012-08-12
Perhaps you might want to try fluxbox rather than openbox? I find the fluxbox configuration much more intuitive although many will disagree :).

---

### Post by urukrama on 2012-08-14
> **c0rnfed said:**
> i already installed openbox and thunar

i want to use these because its not as taxing on my ram as unity is
how do i set my default fm to thunar?
and also how do i remove unity, metacity nautilus?

You don't need to remove Unity to use Openbox. Just select the Openbox session at the login screen instead of the Unity session.

If you need help configuring Openbox, you might find the Openbox guide linked to in my signature useful, even if it is a little outdated.

---

