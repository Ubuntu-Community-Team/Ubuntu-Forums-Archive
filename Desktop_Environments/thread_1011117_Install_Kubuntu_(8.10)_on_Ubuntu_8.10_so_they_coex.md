---
title: "Install Kubuntu (8.10) on Ubuntu 8.10 so they coexist, with Alternate Install CD"
date: 2008-12-14
forum: Desktop Environments
---

### Post by W.Sorting on 2008-12-14
Hello, 

I'm wondering how to install Kubuntu 8.10 on Ubuntu 8.10, so they coexist.  

I want the final configuration to be able to choose between KDE and Gnome at 'sessions'.

I have the Kubuntu 8.10 _**Alternate Install CD**_ available, and I already have an Ubuntu box.  

How do I go about doing this?

I apologize if it's a simple operation-- I'm still a newbie! 

Thank you, 
W.Sorting

---

### Post by Bucky Ball on 2008-12-14
You could just install KDE by itself, 

[http://www.kde.org/download/#v4.1](http://www.kde.org/download/#v4.1)

that could possibly also be in Synaptics along with: 

kubuntu-desktop

Search for that as it will load kde along with the themes, artwork and packages also though.

---

### Post by W.Sorting on 2008-12-16
Yes, but I have the Alternate CD available and downloading KDE would be impractical for me (extremely slow connection).  Is there a way I can do this with only the Alternate CD?

---

### Post by Bucky Ball on 2008-12-17
** I wrote the Alternate Method before I figured out a much simpler way just below, which can be done using the GUI(s) and no terminal. If it doesn't work, try the alternative ...

Head to:

System->Administration->Software Sources (I think, have been using Xubuntu and slightly different setup - you will find Software Sources somewhere).

, unlock and you will see a window at the bottom that says:

To install from cd-rom or a dvd, insert etc, etc,...

Follow your nose. Once this is added to your sources, you may find when you close the software sources window the machine may want to do an automatic update. Do that. The system should check to see what is available to install from the cd. After this you should now be able to go to Synaptic Package manager and find 

kubuntu-desktop

(or you can use 'sudo apt-get install kubuntu-desktop' in a terminal)
along with a lot of other things. You could try looking for just KDE and you might be able to load just that without all the other stuff. Experiment! My desktop is currently an Xubuntu install with the Ubuntu Studio real time kernel (low latency multimedia kernel) and apps installed in that (no Studio desktop, just the apps). It is cool and extra snappy because of the xfce environment. If you're interested in trying a few out, openbox is one I've used and find great. It has KDE/Openbox and Gnome/Openbox environments and it speeds the machine up noticably. 

Alternative method:

This information is from here and was originally for 5.04. THINGS MAY HAVE CHANGED although it probably still works fine. 
[http://ubuntuforums.org/archive/index.php/t-26709.html](http://ubuntuforums.org/archive/index.php/t-26709.html)

insert Kubuntu 8.? CD then in a terminal, (paste a line at a time, not all together):

```
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
```When you are back at the login screen, click 'Session' and there will be a list. One of the entries should be KDE. Select, login. You will be asked if you want to make this permanent or just this session. I would advise 'just this session' to make sure all is working okay with KDE (although this could be one of my strange habits).

Let us know how you went. That will (should) install the package Kubuntu-desktop, which will include KDE, themes, icons, the works. I would imagine there is a way to just install KDE and not everything from the kubuntu-desktop, you could have a browse.

ps: if this doesn't work, a clue is that you need to get the kubuntu cd available in your sources list. If you can do this, you would be able to do an update and search for 'kubuntu-desktop' in Synaptic Package manager (whilst the cd is in, of course). Good luck.

---

### Post by W.Sorting on 2008-12-20
Thank you for the informative post! 

I will try this method as soon as possible.

---

### Post by spectrevk on 2008-12-20
> **Bucky Ball said:**
> You could just install KDE by itself, 

[http://www.kde.org/download/#v4.1](http://www.kde.org/download/#v4.1)

that could possibly also be in Synaptics along with: 

kubuntu-desktop

Search for that as it will load kde along with the themes, artwork and packages also though.

I wouldn't recommend installing the kubuntu-desktop package from Synaptic. KDE will work fine, but when I went back to GNOME, the user switcher was broken.

---

### Post by Bucky Ball on 2008-12-23
> **spectrevk said:**
> I wouldn't recommend installing the kubuntu-desktop package from Synaptic. KDE will work fine, but when I went back to GNOME, the user switcher was broken.

With a bit of tweaking you could probably iron out the bugs. I haven't tried that particular blend before but there are bound to be quirks with various combinations. I personally don't use KDE at all as I find it a little temperamental but my gnome is rock solid. I suppose I could play around and get things just the opposite but sure some people have a stable setup for both. :)

I am normally happy with a selection of my favourite apps and play with desktop managers, themes and artwork based around a set of these.

---

### Post by theozzlives on 2008-12-23
I thought KDE4 was kubuntu-kde4-desktop

---

### Post by Bucky Ball on 2008-12-23
Nope, desktop manager/enviornment. Kubuntu uses KDE as its desktop manager. Try out some others.


[http://www.kde.org/download/#v4.1](http://www.kde.org/download/#v4.1)

---

