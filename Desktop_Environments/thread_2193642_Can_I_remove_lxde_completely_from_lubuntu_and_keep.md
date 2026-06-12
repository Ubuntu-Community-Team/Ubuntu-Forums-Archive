---
title: "Can I remove lxde completely from lubuntu and keep kubuntu-desktop?"
date: 2013-12-13
forum: Desktop Environments
---

### Post by zkr300 on 2013-12-13
I have installed lubuntu that comes with the standard desktop lxde. I have since installed kubuntu-desktop on top of it. If I now remove lxde by virtue of:

sudo apt-get purge lxde
sudo apt-get autoremove

Will this cause conflicts because lubuntu must have lxde to run? Or will it automatically boot to kubuntu-desktop?

Thanks in advance and cheers.

---

### Post by Bucky Ball on 2013-12-14
Not sure. Easier would be to backup and do a clean install Kubuntu.

---

### Post by zkr300 on 2013-12-14
Thanks for the tip but I can't install kubuntu because of older, more inferior hardware. :)

---

### Post by vasa1 on 2013-12-14
My guess is that you can log into a kubuntu desktop session and then "carefully" start deleting things you don't want. Use *apt-get purge **-s** package_name* to get a simulation of what will be deleted and then, based on your assessment of the consequences, do the real thing. 

If I were you, I'd follow Bucky Ball's advice. Clean installs are cleaner :)

---

### Post by vasa1 on 2013-12-14
> **zkr300 said:**
> Thanks for the tip but I can't install kubuntu because of older, more inferior hardware. :)

This is making no sense :(

Can you explain?

---

### Post by codemaniac on 2013-12-14
you can try removing the lxde packages and install kubuntu-desktop. Physocat lists the packages in the below blog.

[http://www.psychocats.net/ubuntucat/tag/pure-kubuntu/](http://www.psychocats.net/ubuntucat/tag/pure-kubuntu/)

I removed all the gtk stuffs from an ubuntu installation couple of weeks ago and installed kubuntu-destop on the system. The only hiccup was the lightdm was still pointing to unity-greeter and it was removed, so no login screen till I changed the greeter-session to lightdm-kde-greeter in /etc/lightdm/lightdm.conf configuration file. 


PS: Please do a backup before everything. :)

---

### Post by zkr300 on 2013-12-14
@vasa i need a non-pae kernel, still have an old celeron processor

---

### Post by zkr300 on 2013-12-14
@codemaniac what do you mean by changing the greeter session and should i do this before hand? 

what is the text that must be replaced?

---

### Post by monkeybrain20122 on 2013-12-14
There may be a simpler way to do it, but here is one suggestion.

Download the rescue CD [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage), make a live usb (check that it boots in your system). Then make a clone of your system with fsarchiver  [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) (probably you only need to clone the / partition if you have separate / and /home) Then do whatever experiments you need to do and if anything goes irreparable wrong just restore the image. If you just clone the / partition it can be very fast to clone and restore and the backup file would not take too much space (mine is about 4 G, the original is almost twice as big)
On restoring I always reformat the targeted partition first.

---

### Post by Bucky Ball on 2013-12-14
> **zkr300 said:**
> Thanks for the tip but I can't install kubuntu because of older, more inferior hardware. :)

? You're running Kubuntu-desktop now. There's not a lot of difference! If you have Kubuntu-desktop installed, you may as well do a clean install of Kubuntu.

---

### Post by monkeybrain20122 on 2013-12-14
> **Bucky Ball said:**
> ? You're running Kubuntu-desktop now. There's not a lot of difference! If you have Kubuntu-desktop installed, you may as well do a clean install of Kubuntu.

I guess what he meant is that Kubuntu doesn't support non pae kernel but lubuntu does, so instead of installing Kubuntn he has to do it in a round about way by installing lubuntu and then switch to a kde desktop.

---

### Post by codemaniac on 2013-12-14
> **zkr300 said:**
> @codemaniac what do you mean by changing the greeter session and should i do this before hand? 

what is the text that must be replaced?

the lightdm configuration file is located in /etc/lightdm/lightdm.conf. I am not sure what lubuntu uses by default, but chances are it uses ***greeter-session=lightdm-gtk-greeter*** in the mentioned config file.

After installing kubuntu-desktop you can change the greeter-session attribute to ***lightdm-kde-greeter***.

---

### Post by mörgæs on 2013-12-14
Here's some info on solving the [PAE]("https://help.ubuntu.com/community/PAE") problem.

---

