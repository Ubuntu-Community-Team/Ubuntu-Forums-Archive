---
title: "What is the easiest way to install Debian?"
date: 2007-07-22
forum: Debian
---

### Post by wersdaluv on 2007-07-22
I always wanted to install Debian, but I am intimidated by its lack if Live CD installers.

What is the easiest way to install Debian?

---

### Post by Steve1961 on 2007-07-22
> **wersdaluv said:**
> I always wanted to install Debian, but I am intimidated by its lack if Live CD installers.

What is the easiest way to install Debian?

Use the netinstall cd image.  You can download it from here:

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

To use the gui just type installgui at the prompt.  It's pretty straightforward these days and much the same as the Ubuntu alternative CD.

---

### Post by abn91c on 2007-07-22
> **wersdaluv said:**
> I always wanted to install Debian, but I am intimidated by its lack if Live CD installers.

What is the easiest way to install Debian?

you can go here for debian live cd's  [http://wiki.debian.org/LiveCD](http://wiki.debian.org/LiveCD)

---

### Post by kinematic on 2007-07-23
you can't install debian from that live cd.

---

### Post by ThinkBuntu on 2007-07-23
How does a LiveCD make installation any easier? I don't understand what you mean there.

Get the DVD 1 for your architecture. It contains 4500 packages, so it's perfect for quickly adding a variety of packages without ever needing to go online. If you want the full package set, get all three DVDs. The only things you'll be missing are encrypted DVD playback, windows codecs (both provided by debian-multimedia.org), and the Flash plugins and Microsoft fonts which both have packages on the disc but require an internet connection to install.

The installer is very easy and straight-forward. From the boot, which is instant, type in "installgui", or "expertgui" for a little more control. Very easy install, in my opinion.

---

### Post by tommcd on 2007-07-24
You can just download the 1st CD from the debian download page and install that. It is a text based installer very similar to the ubuntu alternate install CD. You can use the installgui option with that as well for a gui installer. You will end up with a system that looks and feels very much like a fresh install of ubuntu.

---

### Post by happy-and-lost on 2007-07-24
From a Windows PC with no floppy/CD/USB... I found Debian's install.exe worked beautifully [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

---

### Post by wersdaluv on 2007-07-24
> **happy-and-lost said:**
> From a Windows PC with no floppy/CD/USB... I found Debian's install.exe worked beautifully [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

:lolflag:

That is so nice! 

Too bad I'm already Microsoft-free. :D

---

### Post by cprofitt on 2007-07-24
The net install worked fantastically for me... I was up and running quickly. The default install seems to have a lot more to it than Ubuntu and I think I am sold now -- Ubuntu was a nice 4 month adventure, but I am moving on to Debian.

---

### Post by kerry_s on 2007-07-24
> **PrivateVoid said:**
> The net install worked fantastically for me... I was up and running quickly. The default install seems to have a lot more to it than Ubuntu and I think I am sold now -- Ubuntu was a nice 4 month adventure, but I am moving on to Debian.

the difference is very noticeable isn't it? you can actually see how it's been butchered to make it more user friendly in ubuntu. all that tinkering to make ubuntu nice has really whacked the stability and speed.

---

### Post by rsambuca on 2007-07-24
I have tried out quite a few distros as of late and I think I will check out debian next.  Do you guys recommend stable (etch), testing (lenny?), or unstable (sid).

---

### Post by kerry_s on 2007-07-25
> **rsambuca said:**
> I have tried out quite a few distros as of late and I think I will check out debian next.  Do you guys recommend stable (etch), testing (lenny?), or unstable (sid).

all of the above, i use the etch net installer and add the other repos after. you can use synaptic to do selective upgrades of single apps or full upgrades. using all 3 repo version's always gives you a choice to drop back to should something be wrong with the updated app.

```
# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 xfce-CD Binary-1 20070407-12:12]/ etch contrib main 

deb http://ftp.debian.org/debian/ etch main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free

deb http://ftp.debian.org/debian/ lenny main contrib non-free 

deb http://security.debian.org/ lenny/updates main contrib non-free 

deb http://ftp.debian.org/debian/ sid main contrib non-free 

deb http://www.debian-multimedia.org/ sid main 

```

---

### Post by Pobega on 2007-07-25
> **rsambuca said:**
> I have tried out quite a few distros as of late and I think I will check out debian next.  Do you guys recommend stable (etch), testing (lenny?), or unstable (sid).

I always recommend testing. Stable is only good for those who are running a server, using stable for a desktop-esque system is just dumb, while unstable is only good if you know how to fix problems. The best way to use unstable is to pin packages from testing, but I'd only advise that when you really know what you're doing, otherwise you can easily break your whole system.

[QUOTE=kerry_s]all of the above, i use the etch net installer and add the other repos after. you can use synaptic to do selective upgrades of single apps or full upgrades. using all 3 repo version's always gives you a choice to drop back to should something be wrong with the updated app.[/quote]

That's not really a smart thing to do from a stable system. I mean, it may work, but let's say you install ANYTHING from testing, chances are it will rely on testing's new libc6 and you'll end up having to upgrade your whole stable system just to install this one package. In the end using stable to pin programs from other releases isn't really a good idea, and will result in a broken OS more times than not. I'd advise against it.

---

### Post by Steve1961 on 2007-07-25
Another vote here for testing.  It's up to date and more than stable enough for a desktop system.  I've been running it now for more than a year without issues.

---

### Post by b9anders on 2007-07-25
I am on testing as well - it suits my requirements for being relatively close to the bleeding edge while getting a very stable system. And if I really want a package that's newer and can't wait, the occasional dipping of toes into sid has gone very smoothly for me so far.

I wouldn't recommend mixing stable with testing AND unstable either. A bit of testing to go with stable or a bit of unstable to go with testing works fine but mixing on all three levels is a sure way to run into breakage.

---

### Post by r4ik on 2007-07-25
Try,

[http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch)

Good luck !

---

### Post by rsambuca on 2007-07-25
> **r4ik said:**
> Try,

[http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch)

Good luck !

Thanks for the link, but that looks like a server setup.  I will be using it as a desktop pc!

---

### Post by r4ik on 2007-07-25
You can install the desktop on page 2

---

### Post by rsambuca on 2007-07-25
Thanks for the replies everyone.  I have just downloaded the debian 'Testing' netinstall iso for amd64.  I haven't decided yet if I am going to just install the desktop, or go for a make-work project and do a minimal server install and manually add the packages I need over time (it would probably take me a while to figure out what packages I need).

---

### Post by r4ik on 2007-07-25
The desktop give's you a minimal install.
But anyway good luck !

---

### Post by rsambuca on 2007-07-25
> **r4ik said:**
> The desktop give's you a minimal install.
But anyway good luck !

Ah, so if I click on the desktop environment, it will just install a basic gnome desktop that I can build upon?

---

### Post by r4ik on 2007-07-25
Yes :)

---

### Post by rsambuca on 2007-07-25
Sounds great!  Thanks for the info.

---

### Post by r4ik on 2007-07-25
Glad i could.
Good luck.

---

### Post by rsambuca on 2007-07-25
hmmm...

Installation SEEMED to go off without a hitch.  It appears to boot up fine and goes to the login screen, but after I enter my name and password, no desktop appears.  I just have a mouse cursor (which works) on a baby blue screen.

Unless someone here has any quick ideas, I am going to head over to the debian forums.  Not a good start!

---

### Post by r4ik on 2007-07-26
Try to apt-get the gnome desktop in recov mode

---

### Post by rsambuca on 2007-07-26
Yeah, that is the first thing I tried, but it said it was already installed.  In the end, I just downloaded the etch netinstall cd and it seems to be working perfectly.  After I play with this a bit, I will switch over to testing, and then to unstable.

---

### Post by r4ik on 2007-07-26
i played around with it to and discovered it is so stable i left it to stay.
Agreed it can be boring sometime's but it is alway's there.
So a got myself an argument with the wife and a second computer :)

---

### Post by rsambuca on 2007-07-29
Well, I started over with the 64bit (lenny) testing installation, but went with just a base command line installation.  I immediately changed my sources to the sid (unstable) repositories, followed by a dist-upgrade.  I then added xorg, gdm, gnome-core, sudo (I am still used to ubuntu), and then have been slowly adding stuff as I need it.  I must say you get a pretty quick system when you do it this way.

Things I still find better in ubuntu are:  multimedia codecs - I can't seem to find an equivalent to win64codecs.  Multimedia stuff just seems to be easier in ubuntu overall, especially for 64-bit.

I also like the ubuntu forums much more!

---

### Post by wersdaluv on 2007-07-30
How do I install Debian Sid? I can't find a netinst CD for it.

---

### Post by happy-and-lost on 2007-07-30
> **wersdaluv said:**
> How do I install Debian Sid? I can't find a netinst CD for it.

Daily builds are here: [http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/](http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/)

[Today's i386 sid netinstall.]("http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/i386/iso-cd/debian-testing-i386-netinst.iso")

---

### Post by wersdaluv on 2007-07-30
> **happy-and-lost said:**
> Daily builds are here: [http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/](http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/)

[Today's i386 sid netinstall.]("http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/i386/iso-cd/debian-testing-i386-netinst.iso")

Is Debian unstable advisable for me even if I am not a l33t h4x0r?

---

### Post by Pobega on 2007-07-30
> **wersdaluv said:**
> Is Debian unstable advisable for me even if I am not a l33t h4x0r?

If you're not too knowledgable about the inner workings of Debian, use testing (Lenny). If you know what you're doing, how to diagnose bugs, submit bug reports, and possibly try debugging programs yourself, by all means dive right into Sid.

---

### Post by wersdaluv on 2007-07-30
Thanks. 

Is this where I get Lenny from? --> [http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)

---

### Post by happy-and-lost on 2007-07-30
> **wersdaluv said:**
> Thanks. 

Is this where I get Lenny from? --> [http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)

Indeed it is. Have fun! :guitar:

---

### Post by Epilonsama on 2007-07-30
Im gonna test Etch cuz if i want to install Lenny i might just use Ubuntu cuz i want to see how stable is debian

---

