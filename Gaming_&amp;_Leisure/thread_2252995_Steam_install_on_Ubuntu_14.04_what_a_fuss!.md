---
title: "Steam install on Ubuntu 14.04 what a fuss!?"
date: 2014-11-16
forum: Gaming &amp; Leisure
---

### Post by zircon_34 on 2014-11-16
Its more a comment and solution to my recent experience installing steam. I use Ubuntu 14.04 Gnome and have a GeForce GTX 750Ti.

I tried to install Steam over the software store, first why are there 2 icons?? Then I installed steam, it did simply not start... I deinstalled and tried install using the command line.

```
sudo apt-get install steam
```

which avoids logging in the ubuntu one account...

still did not work. After checking some forums, seems that first I need to deinstall my NVIDIA driver for my GeForce, install steam and then reinstall the NVIDIA driver. Did that and now it works and launches!

Steam on linux is fantastic, but why make it so difficult to install? Especially, using an NVIDIA graphic card, which should be compatible with linux...):P

---

### Post by MikeCyber on 2014-11-17
I remember to use the download from steam working fine but yes lots of apps in synaptic seem outdated. For ex. for Nvidia there were several packages and half was broken some months ago...

---

### Post by oldrocker99 on 2014-11-17
This works:
Go to [http://store.steampowered.com/about/](http://store.steampowered.com/about/) and download **steam_latest.deb.**

Then open a terminal and type:
```
cd (wherever you saved the file)
sudo dpkg -i steam_latest.deb
```
You'll get an error message saying it could not be installed, because of missing dependencies, so, then, type
```
sudo apt-get -f install
```
This should get you off and running; it is how I install Steam on a new installation, and it works every time for me.

Of course, you can make it all one line, thus:
```
sudo dpkg -i steam_latest.deb && sudo apt-get -f install
```

Either way will work, of course. Good luck!

---

### Post by QIII on 2014-11-17
As I recall, the need to remove proprietary drivers has been that way for a while.  I just had to reinstall 14.04.1 (Samsung SSD firmare update -- don't get me started on that) and remembered that was necessary when I reinstalled Steam.

As for why it's so difficult -- that's on Steam and they are the ones to ask.

Cheers!

---

### Post by zircon_34 on 2014-11-18
Hopefully, they will better work together with canonical for better integration. I am not sure everyone is patient to try tweaks for installing steam. Would be nice, especially for newcomers. Anyway, more philosophical than technical...

---

### Post by QIII on 2014-11-18
I don't think it has anything to do with Canonical.

I install Steam directly from Steam's website.

---

### Post by BlinkinCat on 2014-11-18
> **QIII said:**
> I install Steam directly from Steam's website.

Me too - and have had absolutely no problems!

---

### Post by QIII on 2014-11-18
Do you have an ATI card?

---

### Post by mfilacchione on 2014-11-19
> **zircon_34 said:**
> Its more a comment and solution to my recent experience installing steam. I use Ubuntu 14.04 Gnome and have a GeForce GTX 750Ti.

I tried to install Steam over the software store, first why are there 2 icons?? Then I installed steam, it did simply not start... I deinstalled and tried install using the command line.

```
sudo apt-get install steam
```

which avoids logging in the ubuntu one account...

still did not work. After checking some forums, seems that first I need to deinstall my NVIDIA driver for my GeForce, install steam and then reinstall the NVIDIA driver. Did that and now it works and launches!

Steam on linux is fantastic, but why make it so difficult to install? Especially, using an NVIDIA graphic card, which should be compatible with linux...):P


I have had no major problems installing steam from the Software Centrer in Edu  Ubuntu 14.04.1.  I have notice their are two packages listed for it, one  gives you the option to install and the other is blank, not for sure why, that is I am guessing one may had linked to a old version or maybe host that no longer offers it?   

I do have the same issue as you, once installed It does not immediately launch, I have notice that I have to reboot the OS after the install for the program to launch, other then that I have found slight glitches with the interface, but nothing to troublesome.

---

### Post by zircon_34 on 2014-11-19
I found it weird that I had to deinstall/install the graphic card, especially that its a common nvidia gaming card if I am not mistaken. it runs now anyways. for me it was not click and play just saying... I am generally not a complainer;-)

If for some the install worked from the steam site without a glitch but not on the software center has this to do with the packaging method? if yes who runs the packaging of the software center, not canonical?

---

### Post by mfilacchione on 2014-11-19
> **zircon_34 said:**
> Hopefully, they will better work together with canonical for better integration. I am not sure everyone is patient to try tweaks for installing steam. Would be nice, especially for newcomers. Anyway, more philosophical than technical...

I really agree with your statement here. Some die hard Linux fans may find this to be really grouchy but I think it makes a excellent point.  I am a huge Linux advocate but at I feel like the biggest issue with most Linux Os's is the fact that a user "off the street" can not walk up to work station running most versions of Linux with out being some what confused or finding certain task being challenged . I think Ubuntu is one of the Better Os's out of the Linux community, that is in regards to being more user friendly, but their is always room for improvement.

---

### Post by mfilacchione on 2014-11-19
> **zircon_34 said:**
> I found it weird that I had to deinstall/install the graphic card, especially that its a common nvidia gaming card if I am not mistaken. it runs now anyways. for me it was not click and play just saying... I am generally not a complainer;-)

If for some the install worked from the steam site without a glitch but not on the software center has this to do with the packaging method? if yes who runs the packaging of the software center, not canonical?

Personally I am really puzzled why the steam client it's self had issue's with your graphics card? I can see maybe some of the games you maybe trying to play under Ubuntu on it but not the client. As I have stated once steam is installed I do have to reboot but graphics card drivers have never been an issue.  For a few games I have played on Ubuntu (that are offered or not offered through steam), I have had to switch graphics card drives for best performance at times. Though I find this the same for what I would have to do in resetting, settings for the graphics card under windows to get the best gaming performance at times.

---

### Post by sayvanfire on 2015-03-28
i love you

---

### Post by humbug0001 on 2015-03-28
I tried for 3 hours to get Steam installed. (Missing 32-bit libraries: libGL.so.1) it seems to be a common problem with plenty of fixes suggestions. i tried all that i could find until i exhausted Google for fixes.

It still isn't working.

---

