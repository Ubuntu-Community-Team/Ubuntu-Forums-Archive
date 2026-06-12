---
title: "Problems since Breezy update"
date: 2005-12-08
forum: General Help
---

### Post by jbro on 2005-12-08
Hello all,

I'm a fairly new Ubuntu user (started with 5.04) and have had an excellent experience to date. Of all the distributions I've tried out (and there are a lot of them) it is by far the easiest to get up and going. Recently, I noticed that Breezy (5.10) had come out, so I decided to upgrade. I downloaded and burned an ISO and then placed it in the CD ROM drive. It autolaunched synaptic with all the upgrades marked and I proceeded to do the upgrade, seemingly without any hitches.

However, the next time I logged into a Gnome session I found that something was not right. In particular, there were no text or icons on either the task bar or the tool bar, and clicking on my desktop icons did nothing. I could right click the background to get to and use the context menu, but it was impossible to launch anything. I created a launcher, but nothing happened when I clicked on it, just like my other desktop icons. The only way to get out was to kill X with Ctrl+Alt+Backspace. 

One other point - in firefox, there was no text. I saw the underlines for the mnemonics, but no text. I fixed this by uninstalling Firefox from the dist and installing Firefox 1.5 from mozilla.org. I still, though, have not been able to fix Gnome.

As I am new to Gnome (I am used to the Ion 2 window manager) I'm not sure how to recover my Gnome session and would greatly appreciate any hints on how to recover from my Gnome ills.

Oh yeah, if anyone could recommend a good tool for handling init.d stuff, I'd appreciate that too.

Thanks and regards,
Jay

---

### Post by 23meg on 2005-12-08
It's probably a font related problem, but I'm unable to diagnose what exactly it is. For a start, see if you have your regular font folders in place at /usr/share/fonts and the first part of your xorg.conf (the font paths) is intact. Also do a search on the forums to see if anyone else has encountered this if you haven't, and take a look at the "Breezy upgrade notes" thread in special.

> Oh yeah, if anyone could recommend a good tool for handling init.d stuff, I'd appreciate that too.Check out Boot-Up Manager, which has a subforum here.

---

### Post by jbro on 2005-12-09
23meg,

It doesn't seem to be the fonts. I set up a different window manager (Ion2) and under that window manager I can log in and use even Gnome applications with no font problems. I fixed the Firefox problem by uninstalling the Ubuntu Firefox and installing from mozilla.org. I'm thinking perhaps some configuration file weirdness, so I'm going to try deleting some configuration files and seeing what happens.

Thanks,
Jay

---

