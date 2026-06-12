---
title: "Question: Gnome v. KDE (RAM Usage)"
date: 2007-03-21
forum: Desktop Environments
---

### Post by lazyrussian on 2007-03-21
I have 512mb of RAM on my Toshiba A105 S2101 Laptop and I've been a Kubuntu user for the last 3-4 months.

I was wondering which distribution uses less RAM initially - when loading the Desktop environment and when loading the following programs (they are constantly open):
Swiftfox (3-4 tabs)
KCheckGmail
Amarok
Kopete
SuperKaramba
Open Office Word

If I were to run these programs (except SK and KCheckGmail - I'd run alternatives) in Ubuntu, would gnome run faster than KDE?

Right now I am using ~450MB of RAM in KDE.

---

### Post by aysiu on 2007-03-22
With 512 MB of RAM, you probably wouldn't notice much difference in performance between Gnome and KDE.

As far as RAM use goes, Linux will try to use as much RAM as possible, and this will not make your performance slower--quite the contrary, actually. Read more [here](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

---

### Post by lazyrussian on 2007-03-22
Thanks Aysiu!

I guess there is one more question - is there a way to speed up my computer (besides prelinking - installing/uninstalling becomes a hassle)?

---

### Post by aysiu on 2007-03-22
> **lazyrussian said:**
> Thanks Aysiu!

I guess there is one more question - is there a way to speed up my computer (besides prelinking - installing/uninstalling becomes a hassle)?
Maybe disable some boot-time services?

```
sudo apt-get update
sudo apt-get install bum gksu
gksudo bum
``` The rest is self-explanatory. You could also try using *kde-core* instead of *kubuntu-desktop*:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by ComplexNumber on 2007-03-22
another tip is to turn *off* all eye candy - no transparency anywhere, no bouncing cursors, etc.

---

### Post by igknighted on 2007-03-22
> **lazyrussian said:**
> I have 512mb of RAM on my Toshiba A105 S2101 Laptop and I've been a Kubuntu user for the last 3-4 months.

I was wondering which distribution uses less RAM initially - when loading the Desktop environment and when loading the following programs (they are constantly open):
Swiftfox (3-4 tabs)
KCheckGmail
Amarok
Kopete
SuperKaramba
Open Office Word

If I were to run these programs (except SK and KCheckGmail - I'd run alternatives) in Ubuntu, would gnome run faster than KDE?

Right now I am using ~450MB of RAM in KDE.

Initially gnome uses less RAM.  However, how much do you love Swiftfox and OO.o Writer?  KDE loads more libraries initially into RAM than Gnome, hence the initial difference.  But they share better, so if you use lots of KDE apps (as you seem to) then they perform far better than Gnome, running gnome equivalents.  I mention OO.o and swiftfox because these to programs are huge memory hogs.  Switching to Kword (or whatever the Koffice word processor is) and using Konqueror as a web browser on KDE would probably be optimal for you.  Using Abiword and epiphany as alternatives on gnome (as well as gaim for kopete) would also run very well.

---

### Post by aysiu on 2007-03-22
> **ComplexNumber said:**
> another tip is to turn *off* all eye candy - no transparency anywhere, no bouncing cursors, etc.
If you're using KDE, there's a little wizard for this. ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer &
``` I think the second part of the wizard asks for how many "effects" you want. I'd advise turning off pretty much everything except desktop wallpaper.

---

### Post by lazyrussian on 2007-03-22
Thank you both! I will look into this later today and post my results.

As for using OO.o and Swiftfox - they are a must.

I need OO.o for school - I think it's lightyears a head of Kword...
I'm a firefox developer and I use alot of firefox-ish features - swiftfox is a must.

---

### Post by moore.bryan on 2007-03-22
*if you're all about speed, you could try openbox ([http://icculus.org/openbox/](http://icculus.org/openbox/)) instead of gnome or kde...*

---

### Post by aysiu on 2007-03-22
Or IceWM. That's what I use.

---

### Post by wieman01 on 2007-03-22
Pretty themes for IceWM... 

[http://themes.freshmeat.net/browse/925/]("http://themes.freshmeat.net/browse/925/")

Have not used it in year, but used to like it a lot for its simplicity & performance.

---

### Post by lazyrussian on 2007-03-27
Alright, well I sped up my Kubuntu without doing too much. When I;m running 4 widgets in super-karamba and swift fox I'm using about 32% of my ram, with kopete and open office open that jumps closer to 50. I've stabilized it more or less - it never goes higher than 60%. 

Thanks for all your help!

---

