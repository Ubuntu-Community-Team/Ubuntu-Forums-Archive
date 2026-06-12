---
title: "Help Needed Customizing..."
date: 2012-10-27
forum: Desktop Environments
---

### Post by Sparrow40k on 2012-10-27
Hey, I'm Blake.

I'm very new to Ubuntu and Linux (I've actually had it since 8.04 but never used it as my main OS with no windows) and I want to change my desktop from this:

*(edit: see first attached image)*

To this:
*(edit: see second attached image)*


I know only very little things about linux desktop like there are things like Gnome, KDE, etc... And I know I'm running Unity. But I have no idea how to accomplish this.
I found this website with some information about the theme: [http://maketecheasier.com/10-of-the-best-linux-desktop-customization-screenshots-to-inspire-your-creativity/2008/11/28](http://maketecheasier.com/10-of-the-best-linux-desktop-customization-screenshots-to-inspire-your-creativity/2008/11/28)  - 1) My Desktop by ramios

Can any one help?

---

### Post by Sparrow40k on 2012-10-27
Any one?

---

### Post by ccrs8 on 2012-10-27
Well, the screenshot that represents what you want to get to is from Ubuntu 7.10, which ran mostly vanilla GNOME (from 5 years ago).  The first screenshot you have is from 12.04 or 12.10, which has the Unity interface.  So there's your first hurdle - you'll need to get to a more traditional desktop in order to get something that looks like the second screenshot.

Once you get a more traditional desktop (vanilla GNOME, Mate, Xfce, etc.), then you just need to fiddle with themes, fonts, window manager appearance, and panels.

---

### Post by StoneFoot on 2012-10-27
Could someone point me to resources that could help me with changing to Gnome from Unity.

---

### Post by alanmoore78 on 2012-10-27
This can be done.  What I've done on my laptop is added the KDE desktop environment, also known as Kubuntu.  This works great and so just to keep some variety, I put the XFCE environment on my desktop, also known as Xubuntu.  I have had very little time the last couple of days but I have gone from a bone-stock wubi install on 12.04 on my normally Windows 7 computer to this:

[[img]http://farm9.staticflickr.com/8047/8129630289_211cef44f4_b.jpg[/img]](http://www.flickr.com/photos/36861440@N03/8129630289/)
[screenshot-10272012-2156](http://www.flickr.com/photos/36861440@N03/8129630289/) by [bigbillhell](http://www.flickr.com/people/36861440@N03/), on Flickr

The steps needed to add xubuntu are simple but the way I did it requires entering commands in the terminal.

```
sudo apt-get install xubuntu-desktop
```

Enter your password and let it go through the installation of the XFCE environment.  Then you log out (don't reboot, just log out) and when the login screen comes up, click the white circle next to your login name and select Xubuntu session, then log in with your normal password.  Now you have xubuntu/xfce installed and running.  If you don't like it, you can log back out and back in Unity.  Simple, right?  You can do the same with Kubuntu (KDE) or Lightweight (LXDE).  Other themes like Cinnamon or MATE might be more complicated but I'm saving my learning experiences on those for when I replace my laptop.  I have to kill it first, but it's too slow to live, too rare to die.

Of course you'll probably want to get rid of Unity and any other unwanted DE's later and there are steps you can take to do that.  I followed these instructions...

[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

...then watched some tutorials on YouTube on customizing various other Linuxes like Arch and Mint and Ubuntu...

[http://www.youtube.com/user/LinuxSpatry](http://www.youtube.com/user/LinuxSpatry)

...and made some changes on my system adding Archey, Guake, Bashish, additional styles and themes, moved my panel to the bottom, took away the dock, and I like it like this.  I'm sure I'll keep making changes over time, but doesn't everyone?

---

### Post by Sparrow40k on 2012-10-27
I install Gnome3?

---

### Post by alanmoore78 on 2012-10-27
While I'm sure it's POSSIBLE to get the look you want from Gnome3, I wouldn't even start there, I'd go with KDE or XFCE (Gnome2 based) and then work from there.  Naturally I'm biased, those are the two I'm familiar with.  MATE is also Gnome2 based.  Cinnamon, for example, is based on Gnome3, and while it's terrific in Linux Mint, I haven't seen it with Ubuntu yet.

---

### Post by vasa1 on 2012-10-27
> **StoneFoot said:**
> Could someone point me to resources that could help me with changing to Gnome from Unity.
You should start your own thread stating your own system specs.

---

### Post by Sparrow40k on 2012-10-28
So I should install KDE on my PC? and then just look around for themes?
Oh and a question... Can you have 2 or more desktops showing at once? Like have Gnome and KDE both together showing the desktop?

---

### Post by Sparrow40k on 2012-10-28
These three links were used in the one I want to make.

How do I install them?

[http://gnome-look.org/content/show.php/Overglossed?content=74813](http://gnome-look.org/content/show.php/Overglossed?content=74813)
[http://gnome-look.org/content/show.php/Overglossed+Emerald?content=74873](http://gnome-look.org/content/show.php/Overglossed+Emerald?content=74873)
[http://gnome-look.org/content/show.php/Liquid-Black-Glas+for+AWN?content=76609](http://gnome-look.org/content/show.php/Liquid-Black-Glas+for+AWN?content=76609)

---

### Post by 8grod on 2012-10-28
You can have both KDE and gnome installed, but you can really only run one environment at a time.

I'm a KDE user, so I may be assistance there.
If you have Untiy now, you can install KDE through the package manager of your choice. I tend to prefer using apt-get.

Regards,
L.S.

---

### Post by Sparrow40k on 2012-10-28
I think I might use Gnome 2..


**1.**     *Also is there any performance difference like, would Gnome 3 run better then Gnome 2?*
**2**.     *And seeing that Gnome 3 is out, does that mean that there wont be any updates or support for Gnome 2?*
**3.**     *Is there any way to make Gnome 2 themes work on Gnome 3?*
**4.**     *How could I make my own themes for Gnome 3?*
**5.**     *Doesn't Gnome 3 have much customization? Because when I look around for Gnome 3 themes they all kinda look the same.*

Thanks.

---

### Post by zombifier25 on 2012-10-28
Before someone can answer your question, you need to distinguish between GNOME 3 and GNOME Shell. GNOME 3 is a set of software used to provide a desktop environment, while GNOME Shell is just a user interface for GNOME 3. Other interfaces include GNOME Classic (identical to GNOME 2's default environment), Unity, etc.

GNOME 2 is dead. GNOME 3 has taken over, and if you want the classic interface, use GNOME Classic, or another DE like KDE, Xfce, LXDE, etc.

> **Sparrow40k said:**
> 
**4.**     *How could I make my own themes for Gnome 3?*
**5.**     *Doesn't Gnome 3 have much customization? Because when I look around for Gnome 3 themes they all kinda look the same.*

Thanks.

And then there's GTK+ themes and GNOME Shell themes. GTK+ themes change the look and appearances of applications, while GNOME Shell themes change only the appearance of GNOME Shell. There are a truckload of different-looking GTK+3 themes, so you must have been looking for GNOME Shell themes. GNOME 3 is very customizable.

(There are also Metacity themes, which change the appearances of window titles, but they're irrelevant since most GTK+ themes come with Metacity themes anyway)

---

### Post by Sparrow40k on 2012-11-01
Could you maybe give me some URLs, I can't really find any...

---

### Post by Sparrow40k on 2012-11-05
Okay, I'm now using Gnome 3. I used > sudo apt-get install gnome and then installed Cairo-dock.

---

