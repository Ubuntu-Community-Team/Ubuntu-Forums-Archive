---
title: "Does anyone know of a Swiftweasel How To?"
date: 2009-04-10
forum: General Help
---

### Post by jpoRS on 2009-04-10
Hello,

I want to give Swiftweasel a try, so I downloaded the tarball and tried to compile it as usual, but nothing seems to be working.  I checked the readme, and googled everything I could think of but still no luck.  Does anyone know of a Swiftweasel specific how to, or of some specific trick I must be missing?

Thanks
jim

---

### Post by d_yat on 2009-09-05
Just so you know, I too am having a problem with swiftfox install from the tarball.
I've tried it on my parents' Jaunty install.
However, on my laptop with it's Hardy (8.04) install, it does work.
So, maybe it's the flavour of ubuntu we are using. I'll let you know if I find anything else out... if you are still trying to get swiftWeasel to work that is!

---

### Post by cmost on 2009-09-05
The easiest way to install Swiftfox or Swiftweasel, is to simply use your package manager as usual.

1.  Open a gnome-termnial and type:
sudo gedit /etc/apt/sources.list

2.  Copy and paste the following into the end of the file:

## Swiftfox builds for Debian/Ubuntu
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

## Swiftweasel builds for Ubuntu (replace "jaunty" with your distribution!)
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) jaunty multiverse

3.  Save the file
4.  Open Synaptic (or whatever package manager you prefer) and refresh the list of available packages (i.e., click 'Refresh' or 'Reload' button.)
5.  Search on keyword Swiftfox or Iceweasel and then select the build for your particular architecture.

Alternately, you can go directly to this site and grab the Swiftfox DEB for your system directly, which you can install manually with gdebi.

[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Good luck!
:)

---

### Post by KushedVapors on 2009-09-06
get swiftweasel. better than swiftfox imho. thnx for the repo

---

### Post by d_yat on 2009-09-13
> **cmost said:**
> 

## Swiftweasel builds for Ubuntu (replace "jaunty" with your distribution!)
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) jaunty multiverse



I don't suppose you have tried this? It doesn't work!
Although on a separate note, I have got swiftweasel to work on quite a few machines now, but not on the one PC i want it to work on! But I do now know it has nothing to do with what distribution is used. something odd with my parents PC seems to be the problem.

---

### Post by adaemox on 2009-09-20
Yeah, that repo suggestion doesn't work for ubuntu or debian.

---

### Post by Foolishgrunt on 2009-10-01
Ditto on that swiftweasel repo. I've seen a couple places suggest that same one, but it doesn't seem to lead anywhere. Anyone know where I can find a valid swiftweasel repository?

---

### Post by winotree on 2009-12-16
This site [http://ompolicy.altervista.org/ubuntu/index.php?dir=karmic/](http://ompolicy.altervista.org/ubuntu/index.php?dir=karmic/) has a deb file that'll work [on my device].  I suppose you could change karmic to jaunty or whatever you're using -- here's hoping it works for you.  I'm sorry, I can't remember the person who originally posted this in these forums to properly thank them...

---

### Post by MountainX on 2009-12-16
> **cmost said:**
> 
## Swiftweasel builds for Ubuntu (replace "jaunty" with your distribution!)
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) jaunty multiverse


This repository seems to be missing. (tar.gz files are there, but no debs). Is there an alternative?

---

### Post by scouser73 on 2009-12-16
**1** - Right click & Extract the Swiftweasel tar.gz

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Swiftweasel file that you have just extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username swiftweasel**

[COLOR="Red"]**Obviously the username refers to you.**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Swiftweasel**

**7** - In the Command field type **/opt/swiftweasel/swiftweasel**

**8** - In the Comment field type **Swiftweasel**

You will now have Swiftweasel installed.

---

