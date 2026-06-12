---
title: "Edit Linux to Make Distro"
date: 2009-06-13
forum: General Help
---

### Post by Poyzin on 2009-06-13
Hello. I'm a long time ubuntu user. I plan to create a linux distro. But I don't want to create anything from scratch.
*Is there a way I could modify one of my Ubuntu live CD's (8.10 or 9.04)? Like changing all of the source of the word Ubuntu, images, all the way to how it starts up. And then create an ISO and release it as a distro?

Can this all be done from Ubuntu? Like not editing the C files.

Thanks in advance.

---

### Post by chen74 on 2009-06-13
don't know but would be interesting finding out i'm sure. Good luck with it :O)

---

### Post by night_fox on 2009-06-13
Its reasonably easy to make editions/clones of ubuntu, see stuff like Ubuntu satanic edition, gobuntu, even gaybuntu.

But how would your distro really be any different from ubuntu? Is there a purpose to your distro?

---

### Post by DGortze380 on 2009-06-13
Sure. But why?

Changing the appearance is all well and good, but unless there is some particular function / software package you want to include / remove ... why bother, it's ubuntu with a different theme.

---

### Post by aesis05401 on 2009-06-13
There are a number of ways to begin looking into this, but my suggestion is to do the following:

Install a straightforward desktop VM application (I use VBoxOSE for simple first-blush testing).

Download the latest stable LFS 'book.'

Use a VM environment hosted on your Ubuntu install to work through rolling a complete LFS install.  

The VM aspect is essential to undertaking a long project like your first custom Linux compile, because you can 'save state' to effectively shut down the VM without losing your place.  

When you are done you can either plunge into rolling additional functionality through the 'Beyond' LFS material or you can come back to your full fledged install (ie: Ubuntu) and start looking at paring down your personal distro based on the low level knowledge you picked up rolling an LFS install.

Whatever you do, attempting to 'understand' Linux at a fundamental level is often best in a restricted environment.  The point of Ubuntu is to offer a very rich environment, and I suspect you will have a difficult time molding your distro until you understand kernelspace/userspace/security models that are very clearly defined in a stripped down Linux environment.

---

### Post by aysiu on 2009-06-13
This can easily be done. I wouldn't call it a distro. It's more like a Ubuntu remix (at least [that's what Ubuntu wants you to call it](http://www.ubuntu.com/aboutus/trademarkpolicy)).

I would recommend [using Remastersys to make your remix](http://www.psychocats.net/ubuntu/remastersys).

---

### Post by Poyzin on 2009-06-13
Okay. Thanks I will start looking into what you suggested.

As for the people who asked why... Well, because I want to. Lawl.
If I get into coding applications, I have an idea of a dock kind of thing. But it takes over the entire screen. I don't want to give it away, because it's revolutionary. I want to put it into an OS. And I don't want to create a kernel or anything, I'd rather edit one.

Edit: I found something called reconstructor. I'm going to try it. And use Remastersys to compile it. Thanks everyone!

---

### Post by aysiu on 2009-06-14
I would advise Remastersys over Reconstructor.

Reconstructor is really kind of limiting in terms of what it'll let you do. I've also found it to be extremely slow (or at least to give very little indication of how long it'll take or whether it has just completely frozen).

Remastersys is much easier to use: customize it the way you want, copy config files to /etc/skel, run Remastersys. Then you have your .iso.

---

### Post by Poyzin on 2009-06-14
> **aysiu said:**
> I would advise Remastersys over Reconstructor.

Reconstructor is really kind of limiting in terms of what it'll let you do. I've also found it to be extremely slow (or at least to give very little indication of how long it'll take or whether it has just completely frozen).

Remastersys is much easier to use: customize it the way you want, copy config files to /etc/skel, run Remastersys. Then you have your .iso.

Does remastersys run with Jaunty Jackalope? Because when I did the tutorial there were no config folders.

And does remastersys save the state in which ubuntu is in? Like where toolbars are and stuff? So I can set it up. And what about setting which applications come with it? (I'm asking because I'm not sure.)

And does either let you edit deep into the system? To what words are, how things are displayed? Right-Click options? Thanks.

---

### Post by aysiu on 2009-06-14
> **Poyzin said:**
> Does remastersys run with Jaunty Jackalope? Yes, in fact I have used it only with Jaunty. > Because when I did the tutorial there were no config folders. You may have missed the step about showing hidden files (see attached screenshot)

> And does remastersys save the state in which ubuntu is in? Like where toolbars are and stuff? Only if you copy those hidden config files to /etc/skel > And what about setting which applications come with it? (I'm asking because I'm not sure.) Yes, all the system files will be saved, including all applications installed.

> And does either let you edit deep into the system? To what words are, how things are displayed? Right-Click options? Thanks. Yes, all the system files will be saved exactly as you have edited them.

I used Remastersys to make a tweaked version of Jaunty for the HP Mini 1120nr (with workarounds for sound problems), and I edited system files, installed and removed applications, changed repositories, and all of those changes (along with the user settings copied to /etc/skel) show up in the remastered .iso.

---

### Post by Poyzin on 2009-06-14
> **aysiu said:**
>  You may have missed the step about showing hidden files (see attached screenshot)
I did that. :P



And thanks! So cool of you to suggest this thing. Yay for OS improvement :P!

---

