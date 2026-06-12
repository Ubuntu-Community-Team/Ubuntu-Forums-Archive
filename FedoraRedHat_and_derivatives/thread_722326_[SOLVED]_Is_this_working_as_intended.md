---
title: "[SOLVED] Is this working as intended?"
date: 2008-03-12
forum: Fedora/RedHat and derivatives
---

### Post by namegame on 2008-03-12
I have recently been experimenting with different Linux distributions, to find which one suited me best. I love the user-friendliness and community of Ubuntu. I have tried Ubuntu, Kubuntu, and Xubuntu. However, I was crushed to find that I would not be able to play my favorite games (WoW and EVE). 

In Ubuntu, 
```
[jeremiah@linux] glxinfo | grep rendering
direct rendering: No

```

However, I recently gave Fedora 8 a try, and got this:

```
[jeremiah@localhost ~]$ glxinfo | grep rendering
direct rendering: Yes
```

I was just wondering if this is working as intended, or is Fedora/Ubuntu acting crazy?

---

### Post by erginemr on 2008-03-12
I presume you have already installed (K/X)Ubuntu to your hard drive and not trying it still from the Live CD environment.

What is your graphics card and what is the outcome of the following command?
```
lspci | grep -i vga
```

---

### Post by namegame on 2008-03-12
Yes, I have tried all of these as actual installations, on separate partitions.

My graphics card: Intel Mobile GM965/GL960 Integrated graphics controller.

As for the terminal output, I am not currently on my linux box, so I'll have to get back to you on that.

---

### Post by sandysandy on 2008-03-12
r u using wine.

regards

---

### Post by ShodanjoDM on 2008-03-12
> **namegame said:**
> Yes, I have tried all of these as actual installations, on separate partitions.

My graphics card: Intel Mobile GM965/GL960 Integrated graphics controller.

As for the terminal output, I am not currently on my linux box, so I'll have to get back to you on that.

Have you installed the xserver-xorg-video-intel driver?

```
sudo aptitude install xserver-xorg-video-intel
```

---

### Post by Antman on 2008-03-12
WOW works fine for me in Ubuntu 7.10. It looks as though you do not have your 3d graphics card drivers installed correctly.

I just used Envy to setup my video (ATI/nVidia) as needed.

---

### Post by namegame on 2008-03-13
I don't know what is going on. I have noticed that in Gutsy, I can not enable visual effects, however in Hardy, I can, so the future shows improvement. However, I have decided to abandon Fedora, for the time being, the support just isn't as strong as it is here, and my college officially supports Ubuntu and Solaris, and no other linux distros, so I'll just stick with what I have.

Thanks for all of your help.

namegame

---

### Post by RebounD11 on 2008-03-13
> **namegame said:**
> I don't know what is going on. I have noticed that in Gutsy, I can not enable visual effects, however in Hardy, I can, so the future shows improvement. However, I have decided to abandon Fedora, for the time being, the support just isn't as strong as it is here, and my college officially supports Ubuntu and Solaris, and no other linux distros, so I'll just stick with what I have.

Thanks for all of your help.

namegame

Your college supports Linux (even if only Ubuntu)?  I want in :D

---

### Post by namegame on 2008-03-14
> **RebounD11 said:**
> Your college supports Linux (even if only Ubuntu)?  I want in :D

yeah, it's great, you can go to our computer science building, and there are offices with clearly posted signs saying (DO NOT ASK ME WINDOWS/NOVELL QUESTIONS) We have a unix help desk, we have an linux users group, some professors even require that you have it installed, or a dual-boot.

---

### Post by erginemr on 2008-03-14
For sketchy Compiz support with Intel Mobile GM965/GL960 and to enable direct rendering:
[http://forum.compiz-fusion.org/showthread.php?t=6725](http://forum.compiz-fusion.org/showthread.php?t=6725)
[http://forum.compiz-fusion.org/showthread.php?p=42412](http://forum.compiz-fusion.org/showthread.php?p=42412)

and to remove the blacklist on the card:
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)
[http://ubuntuforums.org/showthread.php?t=619099&page=2](http://ubuntuforums.org/showthread.php?t=619099&page=2)

---

### Post by dca on 2008-03-14
> **namegame said:**
> yeah, it's great, you can go to our computer science building, and there are offices with clearly posted signs saying (DO NOT ASK ME WINDOWS/NOVELL QUESTIONS) We have a unix help desk, we have an linux users group, some professors even require that you have it installed, or a dual-boot.

Clearly this is not in the US...
 
...however, I do have a valid passport... :D

---

### Post by namegame on 2008-03-14
> **dca said:**
> Clearly this is not in the US...
 
...however, I do have a valid passport... :D

Oh yeah, it's in the US, I see you are from Orlando, surely you have heard of Clemson University, with the Bowden rivalry and all...

Here is a link to one of the linux pages.

[Link]("http://ccit.clemson.edu/resources/linux/index.php")

And here is our user's group.

[Link 2]("http://clemsonlinux.org/")

---

### Post by igknighted on 2008-03-14
My school (a smallish state school in NY) is very unix friendly as well.  We have used unix-based systems in every class (CS class at least) and have 3 labs of *nix machines (2 freebsd, one gentoo).  Fedora and Knoppix DVDs are all distributed, and Mandriva, Ubuntu and several others are available for download.  Not to mention there are 4 or 5 *nix specific courses, including one on programming the linux kernel.

---

