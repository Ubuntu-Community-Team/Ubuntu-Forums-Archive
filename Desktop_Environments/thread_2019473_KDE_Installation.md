---
title: "KDE Installation"
date: 2012-07-07
forum: Desktop Environments
---

### Post by community on 2012-07-07
Hai,
            I would like to install KDE on my Samsung laptop where Ubuntu 12.04 is presently installed.Which option from the Ubuntu software center should I choose to install it?Or how cant it be done via terminal?

---

### Post by gakon77 on 2012-07-07
Hello,

normally you can find the KDE desktop environment package in you favourite package manager. Just install it and log out,
there should appear a menu (or a button to access it) where to choose descktop environments available.

It you work from the terminal try

```
su apt-get install kde-full
```

if it doesn't work look for it with

```
[s]su[/s] apt-cache search kde
```


If success, as above; you need to restart the windows server X11

---

### Post by lolpenguin on 2012-07-08
```
sudo apt-get install kubuntu-desktop
```
This will install what you get from a fresh Kubuntu install.

---

### Post by drpjkurian on 2012-07-08
Hi
Ia m happy to konw that you are from my native place. well since you have ubuntu 12.04, you can fire ubuntu software centre and type 'kdm' in search bar. you will get an option known as 'KDE Display Manager for X11'. just select and install it by entering your password. Please do not forget to click the addons at the end of the page in the ubuntu software centre window for 'KDE Display Manager for X11'

Well I also used both the display managers earlier but it made my system bloated with lots of packages. I like KDE's beauty but it was not as robust as GNOME. I even once reviewed in one of the thread that "KDE is beautiful but not stable. GNOME is stable but not beautiful"

Now both of my machines are running on GNOME shell with customization.

---

