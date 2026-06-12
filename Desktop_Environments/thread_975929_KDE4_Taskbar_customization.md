---
title: "KDE4 Taskbar customization"
date: 2008-11-08
forum: Desktop Environments
---

### Post by GameKyuubi on 2008-11-08
Hey.  Two questions.

1) Is there a way to add a quicklaunch widget to the KDE4 taskbar?

2) Is there a way to get the TaskManager widget to display in two rows instead of one really huge one?

Thanks
:guitar:

---

### Post by aged hippy on 2008-11-09
1) Yes, select <Unlock Widgets>, then right-click on the Panel ->Add Widgets ->Quicklauncher. :)

2) .... there is a multi-row task manager available, but every time i've tried to <add> it, it has crashed Plasma. :(

---

### Post by stonis on 2008-11-13
There is no Quicklauncher widget. I think this i the main reason why somebody asked this question.

---

### Post by Viranh on 2008-11-13
I have yet to find a way. However, when I added a new panel to the left side of my screen I can drag icons to it to use as a quick launch.

---

### Post by aged hippy on 2008-11-14
> **stonis said:**
> There is no Quicklauncher widget. I think this i the main reason why somebody asked this question.

I apologise. :)

It is easy to take things for granted, if you add these lines to your sources.list there will be.
:D

> 
deb [http://ppa.launchpad.net/samrog131/ubuntu](http://ppa.launchpad.net/samrog131/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/samrog131/ubuntu](http://ppa.launchpad.net/samrog131/ubuntu) intrepid main


There are some other interesting goodies there as well. :)

---

### Post by GameKyuubi on 2008-11-26
I added those lines, but I'm not seeing any difference in my widget list. Do I have to restart or something?

---

### Post by SuperSonic4 on 2008-11-26
You have to update

```
sudo apt-get update
```

---

### Post by GameKyuubi on 2008-11-26
I ran

```
sudo apt-get update
```

and then updated via Adept, but still nothing.  I feel pretty dumb :[

---

### Post by baycoo01 on 2008-11-26
Charge stun. This 1-second stun has been one of the most annoying mechanics in a warrior's arsenal to date.we provide wow gold,cheap wow gold,warcraft gold. Charge is almost mandatory for entering combat effectively and forcing yourself to begin your stun DR (which resets after 20 seconds) with a 1 second stun just so you can get in melee range and generate a little bit of rage off of it seems very counter-productive, especially with a Protection-oriented build with 2 other controlled stuns (concussion blow and shockwave) and for any warrior in general as it shares DR with intercept stun. we provide wow gold,cheap wow gold,warcraft gold.Would it be possible to change Charge into a 1-second immobilize and 2-second interrupt? This would effectively yield the same results even for snare-immune targets (via hand of freedom) but would not annoyingly start your stun DR worthlessly. [wow gold](http://www.baycoo.com)[wow power leveling](http://www.baycoo.com/powerleveling-wow.asp)[wow power leveling 80](http://www.baycoo.com/powerlevelingreport.asp)[wow gold paypal](http://www.baycoo.com/wow_gold_paypal.html)[wow gold reviews](http://www.baycoo.com/wow_gold_paypal.html)

---

### Post by jacksaff on 2008-11-26
That command adds software sources, but not any software. 
No doubt there is a package in there that contains these new widgets and which you can now install using a package manager such as synaptic ... but agedhippy hasn't told us what this package is called. 
While you're waiting you could search synaptic for plasma and see if any new packages show up.

---

### Post by bfg666 on 2009-01-10
> **jacksaff said:**
> That command adds software sources, but not any software. 
No doubt there is a package in there that contains these new widgets and which you can now install using a package manager such as synaptic ... but agedhippy hasn't told us what this package is called. 
While you're waiting you could search synaptic for plasma and see if any new packages show up.

Checking inside [COLOR="Blue"][http://ppa.launchpad.net/samrog131/ubuntu/dists/intrepid/main/binary-i386/Packages]("http://ppa.launchpad.net/samrog131/ubuntu/dists/intrepid/main/binary-i386/Packages")[/COLOR] lists the package we need as "plasmoid-quicklauncher".

> deb [http://ppa.launchpad.net/samrog131/ubuntu](http://ppa.launchpad.net/samrog131/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/samrog131/ubuntu](http://ppa.launchpad.net/samrog131/ubuntu) intrepid main 

So, add the two lines to your sources.list, then:

```
sudo apt-get update
sudo apt-get install plasmoid-quicklauncher
```

Then you should be able to add a quicklauncher plasmoid to the panel.
It's from [COLOR="Blue"][http://www.kde-look.org/content/show.php/QuickLauncher+Applet?content=78061]("http://www.kde-look.org/content/show.php/QuickLauncher+Applet?content=78061")[/COLOR] so please be aware that it is in beta, it is not an official package and the package is not hosted by Ubuntu. As a beta, it's not perfect and you can't drag items from the panel onto it, but you can drag icons from your application launcher. Once setup it seems to work fine.

Hope this works for you too :)

---

