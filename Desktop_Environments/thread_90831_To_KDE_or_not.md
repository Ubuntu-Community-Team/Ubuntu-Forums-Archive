---
title: "To KDE or not"
date: 2005-11-15
forum: Desktop Environments
---

### Post by majkmil on 2005-11-15
I have ubuntu loaded on a 80 gig HD. I want to try Kubuntu out. Can I load the kubuntu cd and repartition the drive so that both OS's have half the space? I am happy with gnome but it looks might I might be missing out by not trying KDE.  Thanks

---

### Post by aysiu on 2005-11-15
You don't have to repartition. Open up a terminal and type this command in ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by nrwilk on 2005-11-15
[QUOTE=majkmil]I have ubuntu loaded on a 80 gig HD. I want to try Kubuntu out. Can I load the kubuntu cd and repartition the drive so that both OS's have half the space? I am happy with gnome but it looks might I might be missing out by not trying KDE.  Thanks[/QUOTE]
That would be completely redundant, because you'd have mostly duplicate files.

I'm not sure which packages you need, but there are several packages you can download to use KDE on your current install.  Most linux distros install both (and others) by default, ubuntu doesn't to save space and make a more specifically developed environment.  In a case where more than one window manager is installed, you just choose the one you want to log into at the login screen.

EDIT: beaten to it.  above is the package you need.

---

### Post by teaker1s on 2005-11-15
i've a kde login manager with metacity and either
gnome
kde
xfce 
 so you can run various desktops

---

### Post by Zerocool10482 on 2005-11-16
In the package manager you can get what every type of desktop environment. I have a ubuntu CD and I turned my other computer into ebuntu. I have KDE and Gnome on the same partions. I like to have both to so my friends can have a easier environment. They like gnome but love eye candy.

---

### Post by majkmil on 2005-11-16
thanks, Hey Fealos, which specific packages are you refering to? I installed the whole Kubuntu Desktop on top of my last Ubuntu install (Breezy). Like you said it seems like I installed alot of duplicate files. I have a very clean install right now and I am hesitant to play with it to much. Are there packages I can install to use the Kubuntu environment without ihstalling the whole Kubuntu-Desktop?
                                                             Thanks  Mark

---

### Post by nrwilk on 2005-11-16
Just take this guy's advice.  Type the two commands he suggests, and you'll have a single install which is capable of booting into both mindow managers.

[QUOTE=aysiu]You don't have to repartition. Open up a terminal and type this command in ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```[/QUOTE]


It sounds like you replaced your ubuntu install with Kubuntu.  If that's true, and you want the Gnome window manager in addition to KDE, then use the following commands to install Gnome:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you do not want Gnome, and you like your Kubuntu install, then do not install anything.  You have everything you need for KDE.  You don't need kubuntu-desktop in that case, because you've already got what it includes.

---

### Post by majkmil on 2005-11-16
Thanks guys, I now have a ubuntu install and want kubuntu AND ubuntu, I will take the advice and install kubuntu-desktop. I was hesitant because my ubuntu install is so clean ( windows fileshaing, network printing, wireless, etc.) I don't want to screw anything up. Will I have a lot of redundent files,programs,etc? Will I need to reconfigure the things above?

---

### Post by Faerine on 2005-11-16
I think you will have redundant programs, like Gaim (instant messenger for Gnome) AND Kopete (instant messenger for KDE), etc. This is what actually prevents me from installing kubuntu-desktop.
On the other hand, there is a kde-core package in 
Synaptic. According to the description "This metapackage includes the core official modules released with KDE. This includes just the basic desktop (browser, file manager, text editor, control center, panel, etc.) and important libraries and data, in addition to the aRts soundserver." Do you guys think it is a good idea to try this one instead of kubuntu-desktop?

---

### Post by incubus on 2005-11-17
I would install either kdebase (which is the very minimum) or kde-core (a little more complete). Then I would progressively install other programs that I might be interested in, such as Kile, Kaffeine, KPDF, etc.

As was pointed out, kubuntu-desktop will install all packages that you have in a fresh Kubuntu installation, and you probably don't need Gaim and Kopete, Adept and Synaptic, and so on. (sorry, I only use Kubuntu, I don't know the other twins out there)

If you get interested in KDE and want to make the appearance of programs more uniform, you can try the gtk-qt engine.

There should be no reason for a problem with having both environments, they both rock and are stable, but I do recomend backing up your /etc and other configuration files regularly. I understand what it is to lose weeks of setting up work. :-)

Good luck!

---

### Post by lerrup on 2005-11-17
Or you could install Kubuntu and then uninstall those you don't like...

---

### Post by Adrian on 2005-11-17
[QUOTE=majkmil]Thanks guys, I now have a ubuntu install and want kubuntu AND ubuntu, I will take the advice and install kubuntu-desktop. I was hesitant because my ubuntu install is so clean ( windows fileshaing, network printing, wireless, etc.) I don't want to screw anything up. Will I have a lot of redundent files,programs,etc? Will I need to reconfigure the things above?[/QUOTE]

No reconfiguration should be necessary. However, your KDE programs will show up in the Gnome menus too. This can be solved as described in the following HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

---

### Post by fishbroetchn on 2005-11-18
what are the pros/cons for kde and gnome. i have not decided yet which i am going to install (dont want both).

i use it for -multimedia (dvds, mp3s, pictures etc)
               -programming (databases, php, c ...)
               -surfing, chatting

i need a x-window which is fast and reliable.

what would u guys suggest??

greets fishbroetchn

---

### Post by mhancoc7 on 2005-11-18
I have been using Ubuntu Hoary Gnome and love it. It is clean and snappy. I recently installed the Kubuntu packages with KDE 3.4. It is really quite nice as well. I had read a lot about the differences. I have to say that both run really nicely on my older Compaq Armada 1750 laptop. In my opinion they both run at about the same speed. I also think that it really depends on your personal choice and less on performance. I like to switch back and forth occasionally to mix things up a bit. However, I think I am going to stick with Kubuntu for now. It is very nicely polished and runs great.

God Bless, Jereme

---

### Post by f1dave on 2005-11-18
[QUOTE=fishbroetchn]what are the pros/cons for kde and gnome. i have not decided yet which i am going to install (dont want both).

i use it for -multimedia (dvds, mp3s, pictures etc)
               -programming (databases, php, c ...)
               -surfing, chatting

i need a x-window which is fast and reliable.

what would u guys suggest??

greets fishbroetchn[/QUOTE]


See, the problem is all you describe here can be done equally as well under both KDE and Gnome!

So it's down to personal preference and whether you like the letter k or g really :P

---

