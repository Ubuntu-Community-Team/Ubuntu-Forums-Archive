---
title: "FPS which is fastest?"
date: 2012-10-25
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2012-10-25
Wrong section sorry for doubleposting:

Hi
I get those results. Anyone confirms or corrects?

Unity                                           30 FPS   FXAA works (only needed for Flightgear)
Gnome 3.6                                 40 FPS   FXAA not working in Flightgear
Terminal desktop                        30 FPS   FXAA not working
KDE (default settings)                 28 FPS
Gnome 2 classic without effects 42 FPS   FXAA works
Fvwm2 crystal                            30 FPS   FXAA not working

Vista 25 FPS
Win8 dev prev 50 FPS !

So why should Linux be fastest?
Cheers

---

### Post by MikeCyber on 2012-11-02
Sorry my fault. Now I get 59 on Windows8 and 62 FPS on Linux. But I wonder if Gentoo or other could even be faster? How much? For 2 fps or so I'd not bother to try.

---

### Post by Linuxisfast on 2012-11-02
Try KDE distro like Chakra, recent tests at Phoronix confirms KDE to be the fastest gaming DE around.

---

### Post by Brebs on 2012-11-02
One should disable vsync, when doing such tests. And state whether vsync has been disabled ;)

---

### Post by MikeCyber on 2012-11-03
vsync? You mean in the game settings?

Chakra, never heard of and I heavily doubt as KDE on Ubuntu 12.10 64bit was slowest. Any link?

---

### Post by holastickboy on 2012-11-03
> **MikeCyber said:**
> Wrong section sorry for doubleposting:

Hi
I get those results. Anyone confirms or corrects?

Unity                                           30 FPS   FXAA works (only needed for Flightgear)
Gnome 3.6                                 40 FPS   FXAA not working in Flightgear
Terminal desktop                        30 FPS   FXAA not working
KDE (default settings)                 28 FPS
Gnome 2 classic without effects 42 FPS   FXAA works
Fvwm2 crystal                            30 FPS   FXAA not working

Vista 25 FPS
Win8 dev prev 50 FPS !

So why should Linux be fastest?
Cheers

These figures are definitely not in line with other benchmarks.  Phoronix is great at benchmarking, and KDE outperforms the others with XFCE just a little behind.  Things like Unity were way back in the pack in terms of performance

Check
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1)

Have you disabled desktop effects with full screen apps in KDE? Have you done the same with Unity or XFCE?  These can really effect your performance a great deal.

I also don't understand the difference between the Windows 7 and 8 scores, there are simply no benchmarks anywhere that puts them within 5 or 6fps of each other in most games (unless there is something really weird with the coding of Flightgear, which in turn would mean it's not the fault of either operating system).

---

### Post by mzrk7 on 2012-11-04
I would have a look at ratpoison :) [http://en.wikipedia.org/wiki/Ratpoison](http://en.wikipedia.org/wiki/Ratpoison)

---

### Post by oldrocker99 on 2012-11-04
For what it's worth, last September Phoronix tested various desktops for speed:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1)

The main thrust of the article is that Unity allowed full-screen games the lowest frame rates, while KDE 4.9 suspended (i.e., in KDE System Settings, Desktop Effects in the Advanced tab, check "Suspend desktop effects for fullscreen windows") gave the fastest frame rates, with LXDE a close second. GNOME Shell was also fast, and came in a close third behind XFCE, with KDE suspended being the fastest in virtually every test.

I know, I didn't expect this result either. However, I did some casual frame rate tests using KDE suspended, and it appears to be true.

Just sayin'.

---

### Post by MikeCyber on 2012-11-05
KDE is a surprise, but also that a simple xterm Desktop does not outperform all, given the fact that it uses the least resources.
[http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html](http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html)

Any ideas why? KDE must be doing something better?

If I could optimize Gnome 3, I'd use that as I'm somehow saturated with KDE.

Also surprising the Intel graphics...I thought they were not very good as for now. Looking forward to the upcoming test with various graphics as well.

---

### Post by holastickboy on 2012-11-05
> **MikeCyber said:**
> KDE is a surprise, but also that a simple xterm Desktop does not outperform all, given the fact that it uses the least resources.
[http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html](http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html)

Any ideas why? KDE must be doing something better?

If I could optimize Gnome 3, I'd use that as I'm somehow saturated with KDE.

Also surprising the Intel graphics...I thought they were not very good as for now. Looking forward to the upcoming test with various graphics as well.

It's all in the coding.  Unity is just not optimised well at this stage, though they have been trying to increase performance recently.

---

### Post by mastablasta on 2012-11-06
i was surpised with KDE on netbook. it was flying.... so i guess they also optimised it for games. suspend effects is a very good idea. i remember in diablo2 in 10.04 i had to do it manually each time before running a game so they didn't interfere...

---

