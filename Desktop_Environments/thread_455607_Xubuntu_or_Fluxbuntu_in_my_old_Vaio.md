---
title: "Xubuntu or Fluxbuntu in my old Vaio?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by ruialexbarbosa on 2007-05-26
Hello,

I own a Vaio N505 Pentium II 400Mhz with 64MB Ram and 10Gb HD.

I installed Xubuntu and put Fluxbox. Now I know there is a Fluxbuntu.

Should I format the HD and install Fluxbox? Or just leave it?

Thanks

---

### Post by madmetal on 2007-05-26
its better to have a clean install on this old laptop...
although with 64mb of ram i suggest either adding another 64mb or try DamnSmallLinux..

---

### Post by ruialexbarbosa on 2007-05-26
I tried SDL, but it is not very user friendly, and my only connection to the internet is wireless, which I use though a Gygabite pcmcia card, and DSL does not recognise it.

Xubuntu just recognizes my hardware out of the box, and I am not a Linux power user... I'm at the copy-paste terminal level...

I can get the extra 64Mb if needed. So you believe it would be faster with a clean Fluxbuntu install? (I don't really care if I'm using more HD space right now. I have enough for my needs (Abiword, Gnumeric, Firefox, Xmedia).

Is there a (much) lighter browser than Firefox? It takes ages to start...

---

### Post by madmetal on 2007-05-26
my suggestion is add another 64mb of ram and use xubuntu...
i also have problems with firefox loading at my armada...

---

### Post by dolphin_oracle on 2007-05-26
I'm running a Vaio with 900mhz AMD duron and 128 mb of ram.  I've got Xubuntu with fluxbox installed.  Works fine.  I've had a few rending issues under xfce, but they are not present under flux.

I also installed fluxbuntu, and I really liked it, except for the fact I never got printing to work right (at all).  Also, the currnt fluxbuntu is based on Dapper, not feisty or edgy.   The standard fluxbuntu install is closer to a ubuntu-server install with Flux and Rox on top.  Fluxbuntu also does not automount usb driver (keys, cameras) out of the box.  And ROX (the file manager) is a matter of taste (I much prefer Thunar).

I second more ram.  Puppy linux would be another option to try.

just my 2 cents.

---

### Post by madmetal on 2007-05-26
memory matters..
i run ubuntu on a celeron 600mhz with 512mb ram , only firefox loads a little slow..

---

### Post by ruialexbarbosa on 2007-05-26
Thanks guys,

One question for you, Dolphin_oracle: I don't need to print, and I want to use dapper (easier to configure network). Would Fluxbuntu be faster, start faster and use less ram than my current xubuntu (dapper) with fluxbox?

---

### Post by dolphin_oracle on 2007-05-26
I've not used plain ubuntu dapper, but I remember thinking it took forever to boot.  I hibenate my xubuntu/flux box mostly, so that feels faster.  fluxbuntu was prettier by default...I really wanted to get it to work for me.  Their site says they are developing a release based on feisty, and I may try it again.

As far as memory usage, I don't remember how fluxbuntu was, but I'ld say since its based on a server install its probably less than my xubuntu/flux combo.  And fluxbuntu does have both the command line package managers and synaptic, so its still easy to get whatever packages its missing that you may need.

Actually, with 64 mb of ram, you probably won't be able to install fluxbuntu- its LIVE CD based with ubiquity (the graphical installer unbuntu uses).  Edgy's LIVE CD install required 192 mb of Ram.  I remmeber the installation on my 128 mb Laptop was very slow.

Here's  a link that may interest you.

[http://www.debianadmin.com/fluxbuntu-light-weight-ubuntu-based-linux-distribution-featuring-fluxbox-window-manager.html](http://www.debianadmin.com/fluxbuntu-light-weight-ubuntu-based-linux-distribution-featuring-fluxbox-window-manager.html)



your 64 mbs is still going to be small for any ubuntu-based system.

---

### Post by kerry_s on 2007-05-26
Just take your time, try and get to know what works and what doesn't. 
How's your experince with linux? If you have enough you might want to go for a custom install.
I'm working on a sony vaio PCG-F430, still learning the quirks of this system. I spent a day running through different linux's and found straight debian seems to be more agreeing for this sony.
Here's the xfce4.iso if you want to try debian on yours, i'm using the net installer  for a custom build up of xfce4, cause i don't need the whole she-bang.

xfce4-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

net installer-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)

---

### Post by ruialexbarbosa on 2007-05-27
Well, that is another thing, I don't have an option to hybernate in fluxbox, and even though XFCE has a hybernate option it does not hybernate...

---

### Post by dolphin_oracle on 2007-05-27
this works for me from the terminal for hibernate (either xfce or fluxbox)

$sudo pmi action hibernate

your mileage may vary.

---

### Post by ruialexbarbosa on 2007-05-27
Mine says it doesn't have enough memory to hibernate... I DO need more ram...

---

### Post by kerry_s on 2007-05-27
I just put the screen to sleep, it's alot easier. :p You can put the screen to sleep on any wm/desktop.

---

### Post by ugm6hr on 2007-05-28
> **ruialexbarbosa said:**
> I tried SDL, but it is not very user friendly, and my only connection to the internet is wireless, which I use though a Gygabite pcmcia card, and DSL does not recognise it.

Xubuntu just recognizes my hardware out of the box, and I am not a Linux power user... I'm at the copy-paste terminal level...

I can get the extra 64Mb if needed. So you believe it would be faster with a clean Fluxbuntu install? (I don't really care if I'm using more HD space right now. I have enough for my needs (Abiword, Gnumeric, Firefox, Xmedia).

Is there a (much) lighter browser than Firefox? It takes ages to start...

I second the either extra RAM or Puppy Linux options.  

Just so you know, Puppy's wireless support was at least as good as Ubuntu at version 2.14 (now 2.16).  I have had it working on a couple of Dell laptops, and also on a desktop with ndiswrapper.  No need for Terminal use either.

As for lightweight browsers - I can recommend Opera.  It's not open source, but it is free (as in you don't have to pay cash for it).  Main issue - no Flash 9 (most sites use Flash 7 anyway).  Otherwise it's excellent on older hardware.  There are even lighter browsers, but, for example Dillo, is unusable for day-to-day surfing.  Opera actually includes a pretty good email program too, as well as a torrent engine (although I found the torrent engine a bit unstable at version 9.10).

PS: If Fluxbuntu is Dapper based - will the wireless still work out of the box?

---

### Post by ruialexbarbosa on 2007-05-28
My Xubuntu/fluxbox is Dapper, and the pcmcia wireless card works out-of-the-box ;)

Is Opera a lot lighter than Firefox?

Can I install puppy linux in the HD?

---

### Post by kerry_s on 2007-05-28
Yes, opera is lighter on old hardware.
Yes, puppy can be installed.

---

### Post by ruialexbarbosa on 2007-05-30
Well, I'm trying puppy now.

I don't have a CD drive, but there's this wake-up disk that puppy provides, and it will let me boot from a USB Pendrive...

Let's see how it goes, I'll come back and tell the tail...

---

### Post by kerry_s on 2007-05-30
> **ruialexbarbosa said:**
> Well, I'm trying puppy now.

I don't have a CD drive, but there's this wake-up disk that puppy provides, and it will let me boot from a USB Pendrive...

Let's see how it goes, I'll come back and tell the tail...

What no cd drive! :( That sucks, vaio's are a bitch to work with, i'm still getting to know this one.(pcg-f430)  :p this things got so many little touchy quirks, then there's that damn propriety button crap, luckly most of mine are working, except all the fn+ f* keys that requires a special driver, not important enough for me to install.

Well i hope you get something you like out of yours.

---

### Post by ruialexbarbosa on 2007-05-31
Damn... Puppy keeps crashing... :( And It's not a lot faster than xubuntu with fluxbox. It also takes longer to boot... Weird.

I'm either trying a xubuntu server install or DSL next...

I installed Xubunto Feisty command line and then synaptic, abiword, xfmedia, gnumeric. It looks faster and lighter.

---

### Post by kerry_s on 2007-05-31
> **ruialexbarbosa said:**
> Damn... Puppy keeps crashing... :( And It's not a lot faster than xubuntu with fluxbox. It also takes longer to boot... Weird.

I'm either trying a xubuntu server install or DSL next...

I installed Xubunto Feisty command line and then synaptic, abiword, xfmedia, gnumeric. It looks faster and lighter.

try the debian xfce4, thats what i'm using right now.
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

---

### Post by ugm6hr on 2007-06-01
> **ruialexbarbosa said:**
> Damn... Puppy keeps crashing... :( And It's not a lot faster than xubuntu with fluxbox. It also takes longer to boot... Weird.

I'm either trying a xubuntu server install or DSL next...

I installed Xubunto Feisty command line and then synaptic, abiword, xfmedia, gnumeric. It looks faster and lighter.

This setup sounds good.  Did you do a server install in the end?  And is this with fluxbox?  Or XFCE4?  If you used fluxbox - what file manager did you use - Thunar?  Does this automount CDs/USBs?

---

### Post by ruialexbarbosa on 2007-06-09
Well, to tell you the truth, I'm still having problems...

I installed Xubuntu Feisty command line (which is the new name for the server install) and am using IceWM as a Window Manager. My problem is I am not a very advanced user and so had to install the Xubuntu Desktop in order to make changes to my system, I guess that slowed everything down.

Thunar automounts my pendrives.

I think the only way to live with 64MB ram is to use Damn Small Linux... :(

---

### Post by ugm6hr on 2007-06-09
I am experimenting with Fluxbuntu on a 128MB desktop, with a view to adding PCManFM instead of ROX (which I believe auto-detects USB media).  Not sure the Fluxbuntu LiveCD will work with 64MB RAM (but possibly with a pre-existing swap).

Ultimately, I want to make use of a very old 48MB RAM PII machine, but figure it's pretty useless without a GUI as a workstation.  DSL runs on it pretty well, but it's just not very friendly.  

PS: I couldn't work out how to make changes in DSL at all.

---

### Post by ruialexbarbosa on 2007-06-14
It has been a rather frustrated atempt, but I'm improving.

The best configuration until now has been Xubuntu with IceWM, Abiword, Thunar, Gnumeric, Vlc, and Epiphany (a LOT lighter than Firefox, Opera, Swiftfox and still very useable). All this with wireless gigabyte card.

---

### Post by malel on 2007-06-15
There is a very good and fast browser to replace Firefox and it is called Swiftfox . It is based on Mozilla . Try it out and I think you will notice it loads very quickly .

Regards

---

### Post by malel on 2007-06-15
There is a nice fast browser called Swiftfox based on Mozilla. I have it running and I am very pleased with it.
Give it a try

---

