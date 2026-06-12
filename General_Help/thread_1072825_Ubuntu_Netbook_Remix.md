---
title: "Ubuntu Netbook Remix"
date: 2009-02-17
forum: General Help
---

### Post by waapwoop1 on 2009-02-17
Hi There,

I was looking at how to isntall the ubuntu netbook remiz on my netbook. I already have 8.10 installed and its great, but would like to get the remix added on.
The UNR help page is very complicated for me.

Is there some script i can type in that will just work, and add the UNR to my Intrepid 8.10 install?

Thanks

---

### Post by earthpigg on 2009-02-17
[https://wiki.ubuntu.com/UNR#Installation](https://wiki.ubuntu.com/UNR#Installation)

i google searched 'ubuntu unr install'

=)

---

### Post by waapwoop1 on 2009-02-17
i read through that.

Is there an easier way, it looks very complicated.

---

### Post by earthpigg on 2009-02-17
> **waapwoop1 said:**
> Is there an easier way, it looks very complicated.

1. Wait for Ubuntu to include UNR in the official repos, so you dont have to add a repo to your sources.list.

=)

otherwise my friend, im afraid the easiest way is to scroll down to "Ubuntu 8.10 (Intrepid) UNR Package Installation" and do those six steps...

---

### Post by waapwoop1 on 2009-02-17
It just says that some don't work for intrepid yet, not sure exactly what to do.

---

### Post by waapwoop1 on 2009-02-17
i think  know waht to do now actually.

---

### Post by biovore on 2009-02-17
Works here on my dell mini 9.

[http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

---

### Post by Tiler on 2009-02-18
Installed from the IMG on my Mini-12.  Install went perfectly but seems to have problems with sources.list.  Does anyone have a list of the sources that are specific to UNR?  My problem is, I don't want to accidentally put the vanilla Hardy sources in there because I didn't convert, I installed clean.

---

### Post by LowSky on 2009-02-18
These steps are very easy just copy and paste the commands

For Ubuntu 8.10 Intrepid Ibex
In a terminal type:

```
sudo gedit /etc/apt/sources.list
```

This will bring up your source list. then add these two lines to the end of your source list:
```
deb http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main
```
```
deb-src http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main
```
In a terminal type:

```
sudo apt-get update
```
To update your source lists.

Then Install the Netbook Remix packages
In a terminal type:

```
sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

FYI: You cant run Compiz and NBR

For Netbook Remix to work you need to set **maximus **and  **netbook-launcher **(if ing 8.10) to your startup programs. Go to **System>Preferences>Sessions **and add entries for both of these commands.

---

### Post by pedja_portugalac on 2009-02-20
I installed UNR from image on my acer aspire one (120GB HDD + 1GB RAM) and I am very impressed by it. It's 3 - 10 times faster then linpus lite, originally shiped with AAO and allow one to have fully featured Ubuntu on netbooks but with specially tweaked gnome for small screen resolutions. In fact, I was so impressed by this powerful and beautiful ubuntu remix that I can't understand why Acer haven't choose it for AAO? I recommends UNR to anyone on any netbook. 

More info on: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

[img]https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-desktop-small.png[/img]

---

### Post by onero on 2009-02-20
That looks great! Did you have to do any tweaking for the Aspire One? I've been trying to decide what distro to install on my newly-purchased AAO, and if it's easy to install, I'm in :D

> **pedja_portugalac said:**
> I installed UNR from image on my acer aspire one (120GB HDD + 1GB RAM) and I am very impressed by it. It's 3 - 10 times faster then linpus lite, originally shiped with AAO and allow one to have fully featured Ubuntu on netbooks but with specially tweaked gnome for small screen resolutions. In fact, I was so impressed by this powerful and beautiful ubuntu remix that I can't understand why Acer haven't choose it for AAO? I recommends UNR to anyone on any netbook. 

More info on: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)



---

### Post by pedja_portugalac on 2009-02-20
Maybe you'll need some tweaks for wireless driver rest is OK.

First read this: [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

PS. Normally they say everything work out of the box when you install from image (1GB). If not there's updates as soon as you connect to the internet. My problem was that I was in hotel and I update using wireless connection from my usb wlan card d-link which works good but that way I didn't get update for integrated wifi card. When I back home, maybe I'll have to install from source another driver for that integrated wifi card. Everything als works good and faster compared to limpus lite. I installed firestarter and ubuntu-restricted packages for multimedia codecs and everything rocks. Not even need to tweak fan speed some people have spoken in the past. Just wireless, that's all what happened in my case.

---

### Post by Jeby on 2009-03-06
Hi, believe me or not, but I've installed UNR from repo on my Acer Aspire 1400LC, P4 1.7 GHz with 256MB of RAM ... :) it runs! Don't worrie, is only for testing it! I want to use UNR as a symplified interface for my future little-home-server-basic-media-center pc (such as EeeBox or Nova P22) and control it with wiimote. If you know Remote Buddy for Mac you can easily understand what i'm talking about.

A couple of question:
1) I'm using Intrepid Ibex so, waiting for the updated version of metacity with "alt+tab" to desktop, is it possible to define a keystroke to "go-home"?
2) Do you know some good on screen virtual keyboard?


Thanks,
Jeby

---

### Post by blackened on 2009-03-06
> **Jeby said:**
> Hi, believe me or not, but I've installed UNR from repo on my Acer Aspire 1400LC, P4 1.7 GHz with 256MB of RAM ... :) it runs! Don't worrie, is only for testing it! I want to use UNR as a symplified interface for my future little-home-server-basic-media-center pc (such as EeeBox or Nova P22) and control it with wiimote. If you know Remote Buddy for Mac you can easily understand what i'm talking about.

Have you tried boxee? [http://www.boxee.tv]("http://www.boxee.tv")

> 1) I'm using Intrepid Ibex so, waiting for the updated version of metacity with "alt+tab" to desktop, is it possible to define a keystroke to "go-home"?...

You should already be able to do that: Sytem->Preferences->Keyboard Shortcuts.
[ATTACH]105525[/ATTACH]

Change the setting I have selected. It should drop you straight to the netbook-launcher from any other window.

---

### Post by Jeby on 2009-03-06
> **blackened said:**
> Have you tried boxee? [http://www.boxee.tv]("http://www.boxee.tv")

yes (on Mac)! But what if I want to launch Me TV, or another app or script? Boxee, XBMC, Elisa, etc are only media center, I want something to access almost *everything* with my Wiimote!
Yes I know, I'm crazy! :D


> **blackened said:**
> You should already be able to do that: Sytem->Preferences->Keyboard Shortcuts.
[ATTACH]105525[/ATTACH]

Change the setting I have selected. It should drop you straight to the netbook-launcher from any other window.

Thanks!! :popcorn:

ps: sorry for my bad English, I'm Italian.

---

### Post by blackened on 2009-03-06
> **Jeby said:**
> yes (on Mac)! But what if I want to launch Me TV, or another app or script? Boxee, XBMC, Elisa, etc are only media center, I want something to access almost *everything* with my Wiimote!
Yes I know, I'm crazy! :D

Whatever turns you on. I've never bad-mouthed anyone who wanted *more* control over their system.

> 
Thanks!! :popcorn:

ps: sorry for my bad English, I'm Italian.

You're welcome, and don't worry about it. Practice makes perfect.

---

### Post by Danny Rafferty on 2009-03-08
I too am on an Acer Aspire One, and am impressed with it.
I have installed UNR following the excellent instructions on this thread, and it seems to have worked, however all is not smooth.
When I initially boot, I still see my old desktop in the background for a while.
Then the UNR interface comes up - a little bit slowly to be honest.
The standard launch bar is at the top, not what I have been seeing on all the posts relating to UNR.
A lot of the time the bar fades out completely and remains invisible.
Launching and changing betweens apps can be slow and produces similar screen effects - like loosing the menu bar at the top of Firefox.
It looks like some sort of window manager issue, but I'm fairly new to linux so am not sure what to do.
Maximus is running as is Netboook launcher.
Is there something I should be turning off perhaps?

Danny

---

### Post by blackened on 2009-03-08
> **Danny Rafferty said:**
> I too am on an Acer Aspire One, and am impressed with it.
I have installed UNR following the excellent instructions on this thread, and it seems to have worked, however all is not smooth.
When I initially boot, I still see my old desktop in the background for a while.
Then the UNR interface comes up - a little bit slowly to be honest.
The standard launch bar is at the top, not what I have been seeing on all the posts relating to UNR.
A lot of the time the bar fades out completely and remains invisible.
Launching and changing betweens apps can be slow and produces similar screen effects - like loosing the menu bar at the top of Firefox.
It looks like some sort of window manager issue, but I'm fairly new to linux so am not sure what to do.
Maximus is running as is Netboook launcher.
Is there something I should be turning off perhaps?
Danny

Are you running Compiz? That could cause problems with it. Considering you're running maximus, it's probably a silly question.

The nebook-launcher does take a short while to come up on my eeepc as well, but this can be attributed (in my case) to the slow SSD it's being booted from.

---

### Post by Danny Rafferty on 2009-03-12
solved.

Blackened YOU DE MAN!

---

### Post by blackened on 2009-03-13
Glad you got it sorted out.

---

### Post by crysys on 2009-03-14
I tried to do something similar to Jeby and install UNR on an Acer Extensa 4420 with an ATI graphics card and 8.10.  When I log in I see a normal desktop for a split second and then the screen is corrupted.  I get nothing but horizontal stripes of colors and occasional flashes of desktop elements.  Could this be a result of UR and compiz running together?  If so, how do I disable compiz from a command line?  It even hangs up when I try to shutdown from the cl.

---

