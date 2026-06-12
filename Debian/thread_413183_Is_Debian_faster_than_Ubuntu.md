---
title: "Is Debian faster than Ubuntu?"
date: 2007-04-18
forum: Debian
---

### Post by Hex_Mandos on 2007-04-18
I'm going to install Linux on an oldish computer (PIII 128 MB RAM). Would you say Debian is faster than Ubuntu, with both using the same DE?

---

### Post by deanlinkous on 2007-04-18
if you load the same desktop AND apps then it will be very close. I certainly would not do a default gnome metapackage on something with that little of ram.

---

### Post by daniel of sarnia on 2007-04-18
And the same kernel version. I've seen benchmarks consistently showing the 2.6.20 kernel preform better on a number of test then the version before it. So if you compare feisty to etch with the same desktop, or none at all, feisty is likely to be faster. But not buy anymore then a few percent difference from what I saw. For example Etch with it's 2.6.18 kernel might encode a 30 MB wav file into ogg in 3 min, where with Feisty and its newer 2.6.20 kernel it might take only 2 min 53 sec to encode the same file. 

Not to much difference but a difference,

---

### Post by koshari on 2007-04-18
> For example Etch with it's 2.6.18 kernel might encode a 30 MB wav file into ogg in 3 min, where with Feisty and its newer 2.6.20 kernel it might take only 2 min 53 sec to encode the same file. i dont agree with that analogy at all, 

the only thing that will make a notable difference on this scenario will be services/resources taking clock cycles away from the process. i hardly think a difference in kernel will make any difference,

---

### Post by aysiu on 2007-04-19
If you have only 128 MB of RAM, I'd say the window manager (or desktop environment, if you dare) and programs you choose would affect performance more than the distribution you choose.

Debian lceWM, Leafpad, Rox-Filer, Dillo will be faster than Ubuntu Gnome, Gedit, Nautilus, Firefox... just as Ubuntu IceWM, Leafpad, Rox-File, Dillo will be faster than Debian Gnome, Gedit, Nautilus, Firefox.

---

### Post by Hex_Mandos on 2007-04-19
No, I'd never dare to use Gnome on that computer. Though I got a working Etch w/Gnome with a PII/256 megs. I just said Ubuntu because I consider the official derivatives to be the same distro... the packages are the same, after all.

I was just wondering. In the same PII I mentioned, SUSE would crawl, but Debian/Gnome worked fine, but I never installed Ubuntu w/Gnome on it (I did try Xubuntu, which was ok).

---

### Post by aysiu on 2007-04-19
And what I'm saying is that it doesn't matter if you're using Debian or Ubuntu.

What matters is what window manager or desktop environment you run and what programs you use.

If you're considering going with Ubuntu instead of Debian, this may help:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Hex_Mandos on 2007-04-19
Aysiu: I know that a lighter WM/DE + lighter apps will run faster. I was just curious about Debian itself, since I've seen it run faster than other distros using the SAME DE. Thanks for the mininimal install image, though I'm a bit skeptical: I've tried to make server installations (of Dapper, Edgy and Feisty), and the install script always fails to detect my network (Desktop disks do this flawlessly). I'll give it a try.

---

### Post by mips on 2007-04-19
> **Hex_Mandos said:**
> I'm going to install Linux on an oldish computer (PIII 128 MB RAM). Would you say Debian is faster than Ubuntu, with both using the same DE?

Try [http://fluxbuntu.org/](http://fluxbuntu.org/)

I would not say you will notice a significant difference in speed between Ubuntu&Debian if your desktop and apps are the same.

---

### Post by rplantz on 2007-04-19
To give you an example of how important applications are, a few months ago I was trying to decide if I wanted to switch to gentoo for the (supposed) speed. (This is from my memory. The details could be off a bit, but the principle is correct.)

I'm working on a 450 page book written in LaTeX. I timed LaTeX's processing of the source. It took 25 seconds under Ubuntu and a little over a minute under Gentoo! This did not make sense. Then I realized that I was using GNOME Terminal under Ubuntu and the xfce4 Terminal under Gentoo. When I switched to GNOME Terminal under Gentoo, it also took 25 seconds to process the book source.

In other words, I was measuring the difference in speed between two different terminal emulator programs, not the difference between two distros.

---

### Post by Hex_Mandos on 2007-04-19
rplantz: I would've thought that the xfce4 terminal would be faster than Gnome's. That's interesting.

---

### Post by rplantz on 2007-04-19
> **Hex_Mandos said:**
> rplantz: I would've thought that the xfce4 terminal would be faster than Gnome's. That's interesting.

Surprised me, too. I have used xfce4 in Ubuntu, Debian, and Gentoo. I don't find it any faster than Gnome. This could be because I have reasonably fast hardware, so any differences are minor.

Of course, the whole point of my comment is that assessing speed is quite complex. I recall a program I worked on back in the early 80s. Users complained during beta testing that the system seemed to pause for a half second almost randomly. The system was set up for about twenty terminals, but we had only installed a couple of them. The pause was the system checking to see if any of the other terminals had been turned on yet. We changed the algorithm to check for only one terminal at a time and keep track of where it was in the checking process. The overall code obviously took longer to execute, but the pause was undetectable by the user. So our users thought that the system ran faster.

---

### Post by plb on 2007-04-20
if we are talking in terms of gnome desktops, debian etch defaults to version 2.14. There was a significant speed improvement in version 2.16.

---

### Post by deanlinkous on 2007-04-20
> **plb said:**
> if we are talking in terms of gnome desktops, debian etch defaults to version 2.14. There was a significant speed improvement in version 2.16.
What do I measure to find it?

---

### Post by bwhite82 on 2007-04-20
> **plb said:**
> if we are talking in terms of gnome desktops, debian etch defaults to version 2.14. There was a significant speed improvement in version 2.16.

Gnome 2.16 is easily installed on Debian Etch using backports.

---

### Post by plb on 2007-04-20
That's good to know. Hopefully they get 2.18 soon.

---

### Post by rplantz on 2007-04-22
> **plb said:**
> if we are talking in terms of gnome desktops, debian etch defaults to version 2.14. There was a significant speed improvement in version 2.16.

That seems odd since debian etch feels faster to me than ubuntu feisty. Of course, as I've pointed out above, there could be many other factors.

---

### Post by fwojciec on 2007-04-22
Debian Etch doesn't enable cpu frequency scaling by default, at least it didn't on my laptop - maybe that's why people "feel" that Debian is faster than Ubuntu.

---

