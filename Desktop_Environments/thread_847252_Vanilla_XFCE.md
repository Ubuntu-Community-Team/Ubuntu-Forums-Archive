---
title: "Vanilla XFCE"
date: 2008-07-02
forum: Desktop Environments
---

### Post by tompickles on 2008-07-02
I have installed Ubuntu 8.04, but want to give XFCE a whirl - hopefully to get more performance out of my pc. I performed sudo apt-get install xubuntu-desktop
but this installes ubuntu themed xfce. How do I install a vanilla xfce which will load from selecting it as a new session on GDM.
I like the look of the app icons on the bottom toolbar etc....

---

### Post by overdrank on 2008-07-02
> **tompickles said:**
> I have installed Ubuntu 8.04, but want to give XFCE a whirl - hopefully to get more performance out of my pc. I performed sudo apt-get install xubuntu-desktop
but this installes ubuntu themed xfce. How do I install a vanilla xfce which will load from selecting it as a new session on GDM.
I like the look of the app icons on the bottom toolbar etc....

HI and this link may help
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

---

### Post by tompickles on 2008-07-02
> **overdrank said:**
> HI and this link may help
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

i dont want to remove GNOME - i just want pure xfce as well as my gnome :)

---

### Post by overdrank on 2008-07-02
> **tompickles said:**
> i dont want to remove GNOME - i just want pure xfce as well as my gnome :)

I apologizes for misreading your post. :KS
If you have install xubuntu and choose it from sessions on the login then you have XFCE but you will also see the gnome apps as you will see the XFCE apps from gnome.

---

### Post by tompickles on 2008-07-02
yeh yeh, erm, though the Ubuntu devs have like mucked aroung with XFCE so it looks like [this]("http://www.xubuntu.org/tour") and not like [this]("http://www.xfce.org/images/about/screenshots/4.4-1.png"). I want the second one :)

---

### Post by HeavyAl on 2008-07-02
Easiest way to do this as far as I know is to use Synaptic: 

* Go to System/Administration/Synaptic Package Manager
* In the search box type in XFCE
* eventually you'll get a bunch of packages listed that are related to xfce
* start checking off the ones you want

Ok, that might be a bit vague. There is probably at least one XFCE meta package in the Synaptic list that will install the entire 'base' xfce system. It will actually say in the notes or in the description line that it's a meta package. However, I've found that if you just use a little common sense as you click off the components to install that you can get a working xfce installation without worrying about any of the meta packages.

-------- 

I just found the meta package .. it's actually called xfce4 (latest and greatest) .. so this should do the trick:

* open an xterm
* type this in:

sudo aptitude --install xfce4

or if you're an apt-get kind of guy:

sudo apt-get install xfce4

either one should do the trick.

---

### Post by overdrank on 2008-07-02
> **tompickles said:**
> yeh yeh, erm, though the Ubuntu devs have like mucked aroung with XFCE so it looks like [this]("http://www.xubuntu.org/tour") and not like [this]("http://www.xfce.org/images/about/screenshots/4.4-1.png"). I want the second one :)

If you are speaking of the dock at the bottom of the screen that is AWN I believe and you will have to install it. It does not come default with Xubuntu. Other than that what is the difference you are speaking of between the links.

---

### Post by tompickles on 2008-07-02
[http://www.xfce.org/about/tour](http://www.xfce.org/about/tour)

it doesnt look like its seperate

---

### Post by overdrank on 2008-07-02
> **tompickles said:**
> [http://www.xfce.org/about/tour](http://www.xfce.org/about/tour)

it doesnt look like its seperate

Well if you are speaking of this screen shot
Then yes I believe these are two different type docks and the link shows the add ons. But I do not use XFCE and it has been a couple of months since I had a system that does. Good luck

---

### Post by mali2297 on 2008-07-02
Install the [xfce4 meta package]("http://packages.ubuntu.com/hardy/xfce4"). 

You will have to customize the panels yourself. It is not that difficult; just right-click on a panel and go to *Customize Panel*.

---

