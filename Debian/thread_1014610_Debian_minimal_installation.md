---
title: "Debian minimal installation"
date: 2008-12-18
forum: Debian
---

### Post by Goll on 2008-12-18
My reference: [http://ubuntuforums.org/showthread.php?t=648896]("http://ubuntuforums.org/showthread.php?t=648896")

Base system is installed from minimal Debian install cd.
Restarted.
Added the sources. 

Internet is not working for the installation.
ping [www.google.com](www.google.com) did not work. 

I suppose I'm missing a command to enable a server..
Advice?

Anything is appreciated.

---

### Post by Sorivenul on 2008-12-18
What network hardware are you using (Ethernet/Wireless)?

You may have to manually install wireless firmware if your card is not supported by default.  

If you are using ethernet, the connection should "just work".  

However, run "ifconfig" to check your interfaces, make sure they are up. Then, for the interface you want (we'll call it $INTERFACE), as root run "dhclient $INTERFACE".

---

### Post by Goll on 2008-12-18
> **Sorivenul said:**
> What network hardware are you using (Ethernet/Wireless)?

You may have to manually install wireless firmware if your card is not supported by default.  

If you are using ethernet, the connection should "just work".  

However, run "ifconfig" to check your interfaces, make sure they are up. Then, for the interface you want (we'll call it $INTERFACE), as root run "dhclient $INTERFACE".

Using ethernet. nvidia. (lol, yeh usually does "just work")
That's why I figured it was just a simple command, (or like in Arch) going into connection config and adding dhcp=eth0 etc...

Thanks, I'll try that. And I'll post my results good or bad. Hopefully help the next person this may happen to.

Thanks again.

---

### Post by Goll on 2008-12-18
if config displays: [http://img355.imageshack.us/img355/7760/img4169aq5.jpg]("http://img355.imageshack.us/img355/7760/img4169aq5.jpg")

This is what it looks like when it boots up:
[http://img291.imageshack.us/img291/9057/img4171fp7.jpg]("http://img291.imageshack.us/img291/9057/img4171fp7.jpg")

I've googled ```
not starting internet superserver debian base install
``` but I'm not getting much from looking around..

Is there anyway I can show my whole bootup sequence to you?
I saw that it loaded nvidia devices in the beginning, so I really don't think it's having a problem with my device..

---

### Post by kerry_s on 2008-12-18
so your doing a server? no gui?

try lenny, its a lot better, newer kernel, more supported hardware:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by Pvt_Ryan on 2008-12-18
try:

ifconfig eth0 up
ifconfig eth1 up

---

### Post by Sorivenul on 2008-12-18
> **kerry_s said:**
> try lenny, its a lot better, newer kernel, more supported hardware
I agree with this. The current state of "lenny" is, IMO, very stable, so do not worry about the "RC" status. The default hardware support is world's better than "etch". It is a joy to use as both a desktop or a server.

---

### Post by wolfen69 on 2008-12-20
> **Sorivenul said:**
> I agree with this. The current state of "lenny" is, IMO, very stable, so do not worry about the "RC" status. The default hardware support is world's better than "etch". It is a joy to use as both a desktop or a server.

i agree. i've been using lenny for over 3 weeks now, and it's probably the most stable OS i've ever used. very nice indeed. :)

---

### Post by polmir on 2008-12-20
**Goll**, type in terminal:```
lspci
uname -r
cat /etc/apt/sources.list

```and post output.

---

### Post by stream303 on 2008-12-27
Another option to consider for the easy route, is to install from the XFCE installation image, even if you don't plan to use a desktop environment, and use a window manager instead of XFCE for the most part.

Then, after the installation, grab your favorite window manager.  There are many.  My favorite is IceWM.  Don't spend much time in XFCE, just get to a terminal and download icewm:

```
apt-get install icewm
```

Now logout.  When you get to the GDM login screen, go to the SESSION menu, and tell it to make IceWM the default for logins from now on.

Bingo - a very slim window manager environment.  The nice thing is that you can use XFCE's "mousepad" for a simple gui text editor by calling it up from an xterm:

```
mousepad &
```

You could even start using XFCE's own lighweight gui terminal, but at some point you may just ask yourself if you should run XFCE in the first place? :)

At any rate, this is an alternate way of bringing up a minimal system for exploration, although you lose the learning experience of installing *everything* step by step.

And, if you want to reclaim some disk space, just use apt-get to start deleting obvious things like OpenOffice, Gimp, (or I guess use synaptic if you want to pull that up for package management) and replace them with say Abiword and ImageMagick for instance.  That kind of thing...

It could be a great way to get a very low-memory system up and running for someone who isn't into all the low-level details, but still wants to run and eventually learn from a very basic environment.

---

### Post by Goll on 2008-12-28
> **stream303 said:**
> Another option to consider for the easy route, is to install from the XFCE installation image, even if you don't plan to use a desktop environment, and use a window manager instead of XFCE for the most part.

Then, after the installation, grab your favorite window manager.  There are many.  My favorite is IceWM.  Don't spend much time in XFCE, just get to a terminal and download icewm:

```
apt-get install icewm
```

Now logout.  When you get to the GDM login screen, go to the SESSION menu, and tell it to make IceWM the default for logins from now on.

Bingo - a very slim window manager environment.  The nice thing is that you can use XFCE's "mousepad" for a simple gui text editor by calling it up from an xterm:

```
mousepad &
```

You could even start using XFCE's own lighweight gui terminal, but at some point you may just ask yourself if you should run XFCE in the first place? :)

At any rate, this is an alternate way of bringing up a minimal system for exploration, although you lose the learning experience of installing *everything* step by step.

And, if you want to reclaim some disk space, just use apt-get to start deleting obvious things like OpenOffice, Gimp, (or I guess use synaptic if you want to pull that up for package management) and replace them with say Abiword and ImageMagick for instance.  That kind of thing...

It could be a great way to get a very low-memory system up and running for someone who isn't into all the low-level details, but still wants to run and eventually learn from a very basic environment.

Yeh- I don't like removing stuff, I like adding the only things I need.
So, low level stuff is the life for me. (I like to disable xinit from starting so I can trip a MS user out when I have him start up the comp (or w.e).

I need to find out how to use my printer on Debian. It's working on Ubuntu, but Debian doesn't have the printer drivers in Foomatic.

I found that to extremely frustrating.
I love the minimalist environment even a full installation gives me (so,so)- but a printer not working, just blows me away.


I liked the expert install from the xfce lenny-
thanks.

---

### Post by stream303 on 2008-12-29
> **Goll said:**
> I need to find out how to use my printer on Debian. It's working on Ubuntu, but Debian doesn't have the printer drivers in Foomatic.

Ah yes, been there.  Usually had to pick up the proper ppd file from [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

> I found that to extremely frustrating.
I love the minimalist environment even a full installation gives me (so,so)- but a printer not working, just blows me away.

Be sure to search
[http://forums.debian.net/](http://forums.debian.net/)

There are quite a few mimimalist debian users with some great help.

Printing was always kind of a drag for me too, although once I eventually got cups, hplips, et al installed, it worked ok - trick is to find out exactly what you need. :)

Also, you may want to take a look at OpenSuse's mimimal install - that DOES come with printing installed - all you do is configure it by going into cups with a browser ```
http://localhost:631
```
and away you go.

Or cheat by using yast. :)


You can only do it from the DVD or Net-Install image.  It is kind of a fat light-install which leaves you at TWM initially, but one edit of the /etc/sysconfig/windowmanager to change the default window manager to "icewm-session" and you're in business.

I guess I'm getting off-track with openSUSE, but it can provide a quick way to get a minimal install with printing via cups etc included for you already.

I guess it comes down to how minimal one wants to start out with.  Always a learning experience, that's for sure!

---

### Post by kerry_s on 2008-12-30
>  Debian doesn't have the printer drivers in Foomatic.

why would you think that? 
do you have all the repos on?

i'm using debian lenny.
```
deb http://www.debian-multimedia.org/ testing main 

deb http://ftp.debian.org/debian/ testing main non-free contrib 
# deb-src http://ftp.us.debian.org/debian/ testing main non-free contrib 

deb http://security.debian.org/ testing/updates main contrib non-free 
# deb-src http://security.debian.org/ testing/updates main contrib non-free 

```

---

### Post by Goll on 2008-12-30
> **stream303 said:**
> Ah yes, been there.  Usually had to pick up the proper ppd file from [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)



Be sure to search
[http://forums.debian.net/](http://forums.debian.net/)

There are quite a few mimimalist debian users with some great help.

Printing was always kind of a drag for me too, although once I eventually got cups, hplips, et al installed, it worked ok - trick is to find out exactly what you need. :)

Also, you may want to take a look at OpenSuse's mimimal install - that DOES come with printing installed - all you do is configure it by going into cups with a browser ```
http://localhost:631
```
and away you go.

Or cheat by using yast. :)


You can only do it from the DVD or Net-Install image.  It is kind of a fat light-install which leaves you at TWM initially, but one edit of the /etc/sysconfig/windowmanager to change the default window manager to "icewm-session" and you're in business.

I guess I'm getting off-track with openSUSE, but it can provide a quick way to get a minimal install with printing via cups etc included for you already.

I guess it comes down to how minimal one wants to start out with.  Always a learning experience, that's for sure!

Thanks for that bit of information. 
I'm surprised openSUSE has anything minimal related to it. 
Although I've never liked RPM package management in my experience.
I'll give that a try.

I'm not afraid from starting out minimal. It's just that the ppd was NOT available. (I looked.)
They were saying something about a proprietary driver (of course) but I ignored that route. (Windows gets it free, but us, no way!)

I wanted to figure out how to pinpoint the packages that Ubuntu uses for its printing stuff (I sort of did, but not really-I think you know what I mean)-
I suppose that would require a lot of T and E.


> **kerry_s said:**
> why would you think that? 
do you have all the repos on?

i'm using debian lenny.
```
deb http://www.debian-multimedia.org/ testing main 

deb http://ftp.debian.org/debian/ testing main non-free contrib 
# deb-src http://ftp.us.debian.org/debian/ testing main non-free contrib 

deb http://security.debian.org/ testing/updates main contrib non-free 
# deb-src http://security.debian.org/ testing/updates main contrib non-free 

```

Yes it's there (I have all the repos on), but the drivers for the MP series for Canon's Pixma are not in their database-
So I'd have to figure a way to pull them over from Ubuntu.

Debian is so....
Fantastic(!) @ its deployment/installation-very intuitive, light, wonderful...
I love the ability to enable root (Without doing an expert install through Ubuntu-p in the a).
I love how Easy it is to set up encrpyted lvm management.
I prefered the xfce expert installation (ridding me of deletion procedures.) +1 to their installer.

It's a good run. definitely.

(My printer is a Canon MP450 Pixma).

I figure I'll do another thread eventually- (If I don't find it elsewhere)
About the transferal of drivers.

---

### Post by kerry_s on 2008-12-30
> My printer is a Canon MP450 Pixma

here's the instructions:
[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP450](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP450)

---

### Post by stream303 on 2009-01-01
> **Goll said:**
> Thanks for that bit of information. 
I'm surprised openSUSE has anything minimal related to it. 
Although I've never liked RPM package management in my experience.
I'll give that a try.

Me neither - although if one is used to apt-get, with opensuse use "zypper", ie

zypper update
zypper install htop

etc.  It is a lot faster than in days of old, but if I continue I suppose I should be posting in the opensuse forum here. :)

> Debian is so....
Fantastic(!) @ its deployment/installation-very intuitive, light, wonderful...
I love the ability to enable root (Without doing an expert install through Ubuntu-p in the a).
I love how Easy it is to set up encrpyted lvm management.
I prefered the xfce expert installation (ridding me of deletion procedures.) +1 to their installer.

I agree.  While I can get a minimal install up and running on other distros, I'm not really learning anything - and even more importantly, with Debian things aren't changing every 6 months - so what I do learn tends to have more of a valuable lifespan.

---

### Post by Goll on 2009-01-01
> **stream303 said:**
> Me neither - although if one is used to apt-get, with opensuse use "zypper", ie

zypper update
zypper install htop

etc.  It is a lot faster than in days of old,

Good, then I'll do that next. Excellent.
And thank you.

---

### Post by RJARRRPCGP on 2009-02-14
> **stream303 said:**
> 

Then, after the installation, grab your favorite window manager.  There are many.  My favorite is IceWM.  Don't spend much time in XFCE, just get to a terminal and download icewm:

```
apt-get install icewm
```


I have to warn everybody that just typing the above may result in an unusable desktop, cannot use the mouse and cannot use the keyboard and thus, the only way out is flip the switch on the back of the PSU or press the case reset button!

The probable cause:

**apt-get** didn't install HAL!

---

### Post by kerry_s on 2009-02-15
> The probable cause:

apt-get didn't install HAL!

:lolflag: i blame it on the new xorg, it use to be so perfect.

---

