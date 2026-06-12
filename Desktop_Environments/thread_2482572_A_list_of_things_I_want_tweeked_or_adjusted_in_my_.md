---
title: "A list of things I want tweeked or adjusted in my in my desktop"
date: 2023-01-04
forum: Desktop Environments
---

### Post by raderall on 2023-01-04
Okay this is by no means and emergency so if you see other people with a problem I'd do them first. I'm slowly googling ways to make my desktop even better but there's a lot I do not know and would like assistance with.
So here are the things I want to do

1. I want a superior boot loader. There's one I had in mind but I forgot it's name. I hear it's just a terminal but I do not know if that's a good thing. It would be cool for someone to tell me the name of this one. and If I could set it so if you punch in a code that's invalid that it would give back a small instruction menu and you could set up hot keys such as, F10 for Xubuntu, F11 for Windows, and F2 to go back to the UFFI bios or whatever ect. I believe you'd have to program a script in sudo nano or cat wouldn't you for this?

2. I have Apt-Fast. How do I set it up using that terminal so if I punch in Apt-Get it does the Apt-fast anyhow.

3. I have a few others I'm going to add over the next upcoming days.

---

### Post by TheFu on 2023-01-04
> **raderall said:**
>  
2. I have Apt-Fast. How do I set it up using that terminal so if I punch in Apt-Get it does the Apt-fast anyhow.
 

```
alias apt-get='apt-fast'
```
Add that to your aliases, where ever you keep them.  Sometimes they are in ~/.bashrc and other times they are in ~/.bash_aliases.

WARNINGS from an old guy:
a) It isn't smart to use any alias with exactly the same name as an existing command for a number of reasons.  Until you understand those reasons, best to NOT do this.  
b) If you are typing, why not use 'apt' instead of apt-get?  Save 4 characters and get most of the features from apt-get and dpkg including wildcard support and automatic dependency resolution.
c) If you do need to use the non-aliased command/function, just prepend a \ to the command, so \apt-get will not use the alias.

I've never used apt-fast. Interesting, if you have plenty of bandwidth, I suppose.  Instead, I have apt-cacher-ng which provides a caching repo on my local network. Effectively, only 1 system causes a package to be downloaded, then all the others get it from that cache at GigE speeds.

---

### Post by grahammechanical on 2023-01-04
Linux bootloaders

[https://www.ubuntupit.com/best-linux-bootloader-for-home-and-embedded-systems/](https://www.ubuntupit.com/best-linux-bootloader-for-home-and-embedded-systems/)

I suggest that experiments like this are best done using an install of Linux on a second drive. In this way you will still a working OS. Very few of us on this forum seem to be experts on Grub. Even fewer could give help on these alternative bootloaders.

Regards

---

### Post by raderall on 2023-01-04
systemd-boot! There's another version of it that came out in in the last two years. you instead boot to just a terminal like instantly. and you punch in a phrase to get to your ubuntu or windows environment. I read what you said I'll use tinycore on an SD Card to experiment with this!

---

### Post by oldfred on 2023-01-04
Grub is both a boot loader & boot manager.

There is a gui boot manager, rEFInd.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 
I have rEFInd on a tiny old obsolete flash drive that was too small for anything. I use it for emergency boot.

---

### Post by ActionParsnip on 2023-01-04
What's wrong with GRUB 2?

---

### Post by TheFu on 2023-01-04
> **ActionParsnip said:**
> What's wrong with GRUB 2?

It is too complicated and routinely gets trashed by MSFT patches.

---

### Post by raderall on 2023-01-05
It's fine. but there's ones that load or start up the desktop boot menu list like like instantly. then again I suppose you could just upgrade your hardware specs.

---

### Post by grahammechanical on 2023-01-05
> What's wrong with GRUB 2?

That was my first thought when I read the first post in this thread. Then I thought, Why not? If someone wants to experiment, why not give some help? Take precautions and have fun. When the fun stops - reinstall.

Regards

---

### Post by raderall on 2023-01-18
Hey I got busy for awhile. But now I'm back around? someone said it would better to tell apt to be apt-fast and just remove the "get" from the links. I can do this right? anything to look out for?

---

