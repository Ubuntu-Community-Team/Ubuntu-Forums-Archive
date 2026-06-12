---
title: "Quick Question"
date: 2007-04-15
forum: Desktop Environments
---

### Post by RealG187 on 2007-04-15
[http://en.wikipedia.org/wiki/Image:Xfce-4.4.png](http://en.wikipedia.org/wiki/Image:Xfce-4.4.png)
[http://en.wikipedia.org/wiki/Image:Xubuntu606.png](http://en.wikipedia.org/wiki/Image:Xubuntu606.png)

In the 2 images, one has taskbars at the top and bottom, while the other has only one at the bottom!

Most of the ones here have at the top and botom:
[http://xubuntu.org/screenshots](http://xubuntu.org/screenshots)

except this one: [http://xubuntu.org/files/edgy2.jpg](http://xubuntu.org/files/edgy2.jpg)
but I think that one cuts off,

whats up? Is XFCE only the botom but xubuntu adds the extra bar at the top?


ALso how come [This](http://en.wikipedia.org/wiki/Image:Linux-SuSE-KDE.png) screenshot has the terminal transparent?

---

### Post by aysiu on 2007-04-15
[quote=RealG187]
whats up? Is XFCE only the botom but xubuntu adds the extra bar at the top?[/quote] Xfce is configurable. You can have two taskbars or only one. It's up to you. > ALso how come This screenshot has the terminal transparent? That's not Xfce. That's KDE. It's pretty easy to get the Konsole transparent. It's a setting.

---

### Post by RealG187 on 2007-04-15
Thanks for fixing the title!

Anyways, so you can have 1 or 2, just set it?

And same for transparent [I knew that was KDE, I just added that to my quick question about Desktop Environment, i used KDE in my tags

---

### Post by shae on 2007-04-15
Xfce default is modeled on CDE  which is similar to the first post, just without the panel set to expand full width.  The people who make Xubuntu made the default similar to Ubuntu's Gnome defaults.  This can always be changed and not all distributions use the same setup for the window manager. (example: Zenwalk, KateOS)

For example in openSuse, Gnome's default is only one panel.  These things can be changed and that is the greatest part about linux!

---

### Post by RealG187 on 2007-04-16
[http://en.wikipedia.org/wiki/Image:Xfce-4.4.png](http://en.wikipedia.org/wiki/Image:Xfce-4.4.png)

This one says it's Xfce, it doesnt say if it is xubuntu or another distro..

Anyyways, how can I make my terminal clear, does it use more CPU/RAM/etc?

PS aysiu, ir ur avatar a cat?

---

### Post by aysiu on 2007-04-16
Well, in *that* screenshot, it looks as if everything is transparent, not just the terminal, so I suspect there's Beryl or Compiz running, not just Xfce. Unfortunately, I don't know much about Beryl or Compiz, but there are other people on this forum who do.

And, yes, my avatar is a cat.

---

### Post by ahaslam on 2007-04-16
If you have compositing enabled in your xorg.conf, options for transparencies become available in the settings manager (Window Manager Tweaks). For the fully transparent terminal (shows anything below, not just desktop), terminal release 0.2.6 is required.

PS. Compositing alone should not use more cpu/ram, it just passes the task to your graphics card. Bearing this in mind, it may noticeably affect videos & games, though it depends greatly on the system.

---

### Post by badboy_24u on 2007-04-16
[SIZE="5"][SIZE="4"]Hi, I downloaded and used ubuntu a few days now. But while, trying to fix a sound problem, i accidentally uninstall the "gnome desktop and gdm". now, when i tried to type this, just like what i've read in some forums, "sudo get/apps and so on, i'm getting an error saying that it can't find  the url [www.ubuntu.apps](www.ubuntu.apps) com. now i'm stuck in DOS. please help. i don't want to re install ubuntu again coz i already have tons of persnal files on my system.thank You[/SIZE]

---

### Post by aysiu on 2007-04-16
If you can't connect to the online repositories, that could be bad.

Let's make sure you're using the right command, though. Try this: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
``` If that doesn't work (i.e., it can't connect to the online servers), try this: ```
cd /var/cache/apt/archives
sudo dpkg -i *.deb
``` If that doesn't work... do you have the Alternate CD or the Desktop CD of Ubuntu?

---

### Post by badboy_24u on 2007-04-16
[SIZE="3"]think U 4 your reply.but the thing is that i've already typed  that correctly.my main problem right now is how can my system connect trough repositories when i'm still at the dos window? i mean, is my internet connection still active while i'm in the DOS state? and about the CD, i think i have the desktop edition ver. 6.06 lts.[/SIZE]

---

### Post by aysiu on 2007-04-16
If you're having trouble connecting to the repositories, it should have nothing to do with being at the terminal... unless you connect through wireless and one of the packages you removed had something to do with wireless.

Did you try this? ```
cd /var/cache/apt/archives
sudo dpkg -i *.deb
sudo /etc/init.d/gdm restart
```

---

### Post by RealG187 on 2007-04-16
> **aysiu said:**
> Well, in *that* screenshot, it looks as if everything is transparent, not just the terminal, so I suspect there's Beryl or Compiz running, not just Xfce. Unfortunately, I don't know much about Beryl or Compiz, but there are other people on this forum who do.

And, yes, my avatar is a cat.

i have a crappy vidoe card, dunno if i can use beryl/compiz...

ill try,but if i cant can i just do da  termimal, if so how?

is aysiu a cat name?

---

### Post by ahaslam on 2007-04-17
If your hardware isn't the best, why would you want to add the bloat of Beryl? Just add the following to your xorg.conf:

> Section "Extensions"
    Option	"Composite" "Enable"
EndSection

After rebooting you will have options for window & menu transparencies along with drop shadows in 'Window Manager Tweaks' within the 'Settings Manager' ;)

If you simply want to have a transparent terminal that shows your backdrop that isn't necessary. Just open a terminal selecting; Edit, Preferences,  Appearance, Background, Transparent background. If you want real transparencies for you terminal, the compositing extension is required, along with the current Terminal release 0.2.6.

:popcorn:

---

### Post by RealG187 on 2007-04-17
Where is xorg.conf? If I can run everything fine now, will my Video card do this?

How do I find out my terminal version?I think it's pretty recent cuz I when did [This](http://psychocats.net/ubuntu/kde) it must have updated it, which terminal is this for, I have Konsole and the one from Gnome and I think another one!

---

### Post by ahaslam on 2007-04-17
For your xorg.conf:
> sudo nano /etc/X11/xorg.conf
add my suggestion to the end & save.

Your vga? Well that depends on what it is. Most Nvidia, Ati & Intel chips with the correct drivers will work well. Generally if you have direct rendering enabled it'll work, but the performance will depend upon the card. To check for direct rendering issue th following in a terminal:
> glxinfo
You're looking for 'direct rendering: Yes'

Terminal version? I doubt edgy has the required version for 'real' transparencies, but going to 'Preferences > Help' will confirm/deny that for you. If yo haven't got it, it's readily available & compiles easily, google will be your friend here ;)

---

### Post by RealG187 on 2007-04-17
also what does LTS stand for? Like in "6.06 LTS"

---

### Post by RealG187 on 2007-05-11
An other quick question, what goes LTS stand for in 6.06.1 LTS, whats the .1 mean, is there a .2???

---

### Post by CaveRat on 2007-05-11
LTS= Long Term Support

---

### Post by RealG187 on 2007-05-11
k, so whats the .1 mean?

Also, there isnt support for other versions, not even here?


I kinda thought that [thought maybe Life Time Support, but 3-5 yrs isnt a lifetime], since one thing Dapper prides it self on is the support, how come Dapper has Long Term what makes it so special?

---

### Post by RealG187 on 2007-05-11
Thats kinda what I thought since 6.06 prides it self on great support. I thought something like Life Time Support but 3-5 yrs aint a lifetime...

DOnt older versions have support? Not even here, why does Dapper have LTS, what makes it so special?

---

