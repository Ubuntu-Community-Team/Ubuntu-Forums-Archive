---
title: "KUbuntu Netbook Remix?"
date: 2009-04-28
forum: General Help
---

### Post by ichilton on 2009-04-28
Hi,

Is there a netbook remix version of kbubuntu available?

Thanks,

Ian

---

### Post by EdTheUniqueGeek on 2009-04-28
I am wondering the same thing.
I installed Ubuntu Netbook Remix on my Dell Mini 9 last night and it runs nicely. However, I much prefer KDE over Gnome so a KNR would be great.

---

### Post by nucleuskore on 2009-04-28
I wonder what would happen if you installed the meta-package kubuntu-desktop

---

### Post by snowpine on 2009-04-28
Try installing and running 'netbook-launcher' within a KDE session. My hunch is it will not work so well, because the launcher is heavily dependent on Nautilus and other Gnome components. But it is worth a try I suppose...

---

### Post by EdTheUniqueGeek on 2009-04-28
> I wonder what would happen if you installed the meta-package kubuntu-desktop

I would think it would install the standard, bloated Kubuntu KDE desktop, not the slimmed down Remix version.

---

### Post by snowpine on 2009-04-28
> **EdTheUniqueGeek said:**
> I would think it would install the standard, bloated Kubuntu KDE desktop, not the slimmed down Remix version.

Is there a "slimmed down Remix version"? I thought that's what this thread was about. :)

ps Ubuntu NBR is slower than Ubuntu; it is not "slimmed down" compared to regular Gnome, so I doubt the hypothetical KDE version would be any faster than regular Kubuntu.

---

### Post by nucleuskore on 2009-04-28
> **snowpine said:**
> Is there a "slimmed down Remix version"? I thought that's what this thread was about. :)

ps Ubuntu NBR is slower than Ubuntu; it is not "slimmed down" compared to regular Gnome, so I doubt the hypothetical KDE version would be any faster than regular Kubuntu.

So it's not so slim as it sounds :) Guess that sort's out the OP's question.

---

### Post by sugarland2k on 2009-08-20
I'm running "plain" Kubuntu 9.04 on my Dell Mini 9, 32GB SSD, 2GB RAM and it runs great, after a few updates and tweeks.
I tried Alpha KDE 9.10 but it was a bit too wiggy for me. :)

---

### Post by matthewbpt on 2009-08-20
Karmic will have a Kubuntu Netbook Edition, see [https://wiki.kubuntu.org/KarmicKoala/Alpha4/Kubuntu](https://wiki.kubuntu.org/KarmicKoala/Alpha4/Kubuntu) for details on the current alpha version.

---

### Post by NormanFLinux on 2009-10-02
The beta is available now. I have it running on my Dell Mini 10.

---

### Post by beastrace91 on 2009-10-03
Also just as a heads up the only difference between Ubuntu NBR and normal 32bit is the fact that it has the "netbook launcher" installed (And that it is packaged as a .img instead of a .iso) Other than that it is the standard distro. I install NBR on my EEE but actually ended up removing the netbook launcher because it is cumbersome at best compared to the standard Gnome desktop.

~Jeff

---

### Post by GameManK on 2009-10-03
There will be a Netbook Edition of Kubuntu Karmic, and a beta is now available.  The interface for it is still a work in progress though, so even when it's released it will be a Technical Preview.  Kubuntu 10.04 should have a more official Netbook Edition.

---

### Post by Velveteen on 2009-10-28
Hey, I was wondering if anyone knows either where an .img of the RC KNR is available or how to mount a .iso onto a USB drive in order to boot from that. It looks so good and I want to try it on my netbook, preferably without having to purchase an external CD/DVD drive!

---

### Post by matthewbpt on 2009-10-28
You can get the Kubuntu Netbook Remix RC from [http://releases.ubuntu.com/kubuntu/9.10/](http://releases.ubuntu.com/kubuntu/9.10/)
To boot the image from a usb drive use the "Usb Startup Disk Creator" in System > Adminitration ,  or download the program UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by kitterma on 2009-10-28
[https://wiki.kubuntu.org/Kubuntu/Netbook#Download](https://wiki.kubuntu.org/Kubuntu/Netbook#Download) and Installing

See the downloading and installing section.

---

### Post by Toriam on 2009-12-01
I ran KNR for about 3 weeks on my Acer Aspire One A110, the 9 inch screen, 1.6 gb proc, 512 RAM version. It was still in testing. I liked the interface (I'm a big KDE fan) but many things went wrong (mainly with graphics), and it was easy to crash. Finally, after reinstalling and playing nice with it for about 2 weeks, it wouldn't boot. I haven't gotten into what exactly went wrong. All in all, it's not ready for widespread use at all, and I think being on a higher-spec machine would be much better. My basic little netbook likes the XFCE version of things, maybe when I slap a little more RAm in it it could handle more, as is usually the case. I'm downloading Fedora XFCE as I write, since Xubuntu 9.10 was a little funny after upgrade.

---

### Post by jwm93k on 2010-04-05
Greetings, I have read many things about the possible KDE remix for Kubuntu. I like the screenshots I have seen and I hope it comes out ready to work on the EEE 901 with the 800x600 default screen size. I heard there may be a problem with this screen size. I like the screenshots of the KDE remix as compared to the Ubuntu UNR screen. I have been using the UNR and found it easy to use but a little klunky. I have been hesitant to try the KDE environment. I read of problems with the new KDE version and issues on netbooks. I also tried Mandrivia and was disappointed. Please update this discussion in April 2010 with news on the KDE remix for netbooks and how well it works, especially on ASUS EEE 901 systems. Thank you for you work in these areas. I like not using M$windows.:guitar:

---

### Post by spot-da-haze on 2010-05-21
I've been using the knr on my aspire one I have a few issues with the sound card with 9.10 then I upgraded to 10.04 and now I have issues with a few things then main thing is not being able to costomize the start bar and I can seam to get to my 'news' page any more? Can any one help?

---

### Post by sugarland2k on 2010-09-02
I will try kubuntu-10.04.1-netbook on my Dell Mini 9 and try loading KDE 4.5.1

KDE 4.5.1 Kubuntu 10.04 packages are available in the backports repository, but they are not officially supported as part of the distribution. The development release (Maverick) 10.10 includes KDE 4.5 packages by default.

1. Add the following repository through KPackageKit or using apt-get in a terminal.

sudo add-apt-repository ppa:kubuntu-ppa/beta
Update: It should be the backport repository, not the beta.

sudo add-apt-repository ppa:kubuntu-ppa/backports2. Run a full upgrade using the graphical package manager or the following commands:

sudo apt-get update
sudo apt-get dist-upgrade

I will report my progress... ;)

---

