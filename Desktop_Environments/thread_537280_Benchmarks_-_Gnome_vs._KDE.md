---
title: "Benchmarks - Gnome vs. KDE ?"
date: 2007-08-28
forum: Desktop Environments
---

### Post by wags08 on 2007-08-28
My laptop is several years old and beginning to get a little sluggish...Ubuntu is moving slow.

I've been told that KDE runs faster than Gnome.  I just find this a bit hard to believe, I guess because the appearance of KDE is just more polished than that of Gnome.

Does anybody know of any reasonably-performed benchmark tests of each desktop environment, or can anybody who has used both on the same machine say anything about their peformance?  Perferrably people who haven't used them with Compiz/Beryl.

I've tried Xfce...while the Xubuntu LiveCD actually ran faster than my hard drive installation of Ubuntu, I just didn't really like it.  On top of that, I end up basically reinstalling all of the Gnome/KDE libraries anyway, as there aren't any Xfce programs I saw that were sufficent for some of the things I needed, whereas I can find both a suitable Gnome and KDE application for everything I need.

Thanks for your help!

---

### Post by trippinnik on 2007-08-28
Don't really know about any benchmarks but you can give many options a try and choose watever you like best.  First though Xubuntu's live CD really shouldn't run faster than you're install.  Have you check what services you have running?  The easiest way to do that is click System - Settings - Services.  Also try running top from the command line.  
If you don't find anything you don't need sucking up your resources then try this [http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core) for adding kde (you'll also want to add other kde apps) or sudo aptitude install openbox to install openbox which you can run on it's own or replaces metacity (the WM for Gnome which many people complain about) You can also replace Nautilus with Thunar the file manager in Xfce.  There's a lot more information about lightweight desktop environments as well if you search the forums.  
How much memory do you have?

---

### Post by wags08 on 2007-08-28
My laptop has 256MB of RAM.

I've disabled everything that wasn't necessary in the past, and it hasn't helped much.

I'm really not running that much stuff at a time.  Right now, it's moving slow and I've got: A Firefox window with two tabs open, my Pidgin buddy list, and a terminal window where I'm writing and building some documents in latex.

I format my laptop everytime a new version of Ubuntu comes out, and it runs without any speed issues at all until a 5-6 weeks after the installation and it's like it just hits a brick wall.

---

### Post by loell on 2007-08-28
all gtk based programs are not just for gnome but for xfce too, what programs are you frequently using in gnome?

---

### Post by Griff on 2007-08-28
I have a Compaq Presario 2100 I got back in 2003 for about $1000.  I've run Gnome, KDE, and XFCE on it.  I agree with your comment about XFCE.  It's just not very nice looking.  And KDE does in fact run better on my laptop than Gnome does.  It's strange, but true.

-Griff

---

### Post by GeneralZod on 2007-08-29
"Speed" is remarkably hard to benchmark, beyond easily quantifiable things like e.g. startup time.  Memory usage is also tricky, but has been treated in great detail.  See the links in

[http://ubuntuforums.org/showpost.php?p=2015680&postcount=1235](http://ubuntuforums.org/showpost.php?p=2015680&postcount=1235)

People always just seem to implicitly assume that KDE would be heavier/ slower than GNOME, and I have no idea why.

---

### Post by happysmileman on 2007-08-29
> **GeneralZod said:**
> "Speed" is remarkably hard to benchmark, beyond easily quantifiable things like e.g. startup time.  Memory usage is also tricky, but has been treated in great detail.  See the links in

[http://ubuntuforums.org/showpost.php?p=2015680&postcount=1235](http://ubuntuforums.org/showpost.php?p=2015680&postcount=1235)

People always just seem to implicitly assume that KDE would be heavier/ slower than GNOME, and I have no idea why.

I agree, I'm a KDE user and even I assumed it was slower and heavier than GNOME until I used it for a few weeks. I think it's because it has more features, is more customisable and IMO more pretty.

KDE should be faster though if you use mainly KDE programs, since they share a lot of code (Pretty much all HTML rendering is done by a single library, same with text editing and stuff like that most of time)

---

### Post by trippinnik on 2007-08-30
When I ask are there any services running I don't mean programs that load an icon into the tray, I mean services like apache etc.  The type of slowdown you describe seems to be unrelated to the desktop environment.

---

### Post by miggols99 on 2007-08-30
I think that with KDE you can turn off features which makes it faster. I have used Gnome before (and still have it) but I just find it less configurable. And Gnome can look pretty too..but I think my KDEmod with Compiz Fusion is much better. At the moment my theme is green. I'm usually obsessed with blue (my favourite colour) and I could have it brown if I wanted, or have two panels to make it Gnome like. But I like the double sized panel for some reason...

---

### Post by mandragora on 2007-08-30
Konqueror preloading plays a role in the illusion of faster performance, basically reducing it to an issue of user behavior. Consider if you use Konqueror as your primary web browser, versus using a browser like Firefox. If you don't keep an instance of Firefox running, Konqueror, already loaded in the background, might seem to come up faster.

Just some food for thought.

---

