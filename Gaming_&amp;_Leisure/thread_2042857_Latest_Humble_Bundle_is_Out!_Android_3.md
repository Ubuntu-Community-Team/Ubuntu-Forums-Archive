---
title: "Latest Humble Bundle is Out! Android 3"
date: 2012-08-15
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2012-08-15
> The Humble Bundle
for Android 3

Five amazing games for your mobile delight. We’re bringing you a mountain of entertainment for your Android devices. Pay-what-you-want to get BIT.TRIP BEAT, Fieldrunners, SpaceChem, and Uplink! And if you beat the average price, you also get the beautiful platform-puzzler Spirits! Please note that Uplink and SpaceChem require tablets if your are playing the Android version.

Love your desktop? So do we. Buying the Humble Bundle for Android 3 also gets you the games on Windows, Mac, and Linux! For your listening pleasure, each game also comes with an official soundtrack.

Pay what you want. On their own, these fantastic games and their soundtracks would cost to the tune of $52, but we’re letting you name your price!

The games work great on Android, Windows, Mac, and Linux (system requirements here). Note that this is the initial release for many of the Android and Linux versions of the games. Please be patient while the developers fix any 1.0 bugs as quickly as they can, and don’t hesitate to contact us if you run into any issues.

Support vital charities. You get to decide how your purchase is divided: between the developers, the Child’s Play Charity, or the Electronic Frontier Foundation. And, if you choose, a Humble tip for putting this promotion together is much appreciated!





[http://www.humblebundle.com/]("http://www.humblebundle.com/")

---

### Post by cgolson84 on 2012-08-15
Bought this.  I'm having problems redeeming Fieldrunners on Ubuntu Software Center.  Everything else worked great but Fieldrunners just gives me a "not found".  I am sure this will sort itself out but I figured I'd let anyone buying this know about it.

---

### Post by Dlambert on 2012-08-15
> **cgolson84 said:**
> Bought this.  I'm having problems redeeming Fieldrunners on Ubuntu Software Center.  Everything else worked great but Fieldrunners just gives me a "not found".  I am sure this will sort itself out but I figured I'd let anyone buying this know about it.

It is the first day! ;)

---

### Post by troyready on 2012-08-15
I'm having the same issue -- the rest redeemed without issue, but unable to "see" fieldrunners yet. Hoping for better luck tomorrow.

---

### Post by cgolson84 on 2012-08-15
> **troyready said:**
> I'm having the same issue -- the rest redeemed without issue, but unable to "see" fieldrunners yet. Hoping for better luck tomorrow.

Yea I'm sure it's just a hiccup on Ubuntu's end but it really makes me anxious for Steam on linux to get here.

---

### Post by phrak on 2012-08-15
I find it funny that I found out about this here and bought it before the humble bundle email got to me.

---

### Post by Carborundum on 2012-08-15
I'm having a problem with Uplink; it's not registering mouse clicks in the lowermost (say) 10% of the screen, thereby rendering it effectively unplayable as a lot of menu items are located in that region.

---

### Post by troyready on 2012-08-15
Update on the fieldrunners problem: Fieldrunners still isn't showing up in the software center for me, but following the directions on my subscriptions page (), I was able to manually add the PPA to my software sources and install the fieldrunners package.

---

### Post by shadowjay on 2012-08-16
> **Carborundum said:**
> I'm having a problem with Uplink; it's not registering mouse clicks in the lowermost (say) 10% of the screen, thereby rendering it effectively unplayable as a lot of menu items are located in that region.
```
/path/to/uplink '!graphics_screenwidth' <your_screen_width> '!graphics_screenheight' <your_screen_height>
```
My uplink executable was in /opt/uplink. Use this to set the resolution for uplink, which seems to fix this problem. I'm not sure if the settings persist, so you might have to adjust the settings in the options menu.

---

### Post by Carborundum on 2012-08-16
> **shadowjay said:**
> ```
/path/to/uplink '!graphics_screenwidth' <your_screen_width> '!graphics_screenheight' <your_screen_height>
```My uplink executable was in /opt/uplink. Use this to set the resolution for uplink, which seems to fix this problem. I'm not sure if the settings persist, so you might have to adjust the settings in the options menu.
That fixed it, thanks! And it does seem to be persistent, so that's even better.

---

### Post by qwertyuiop924 on 2012-08-16
> **troyready said:**
> Update on the fieldrunners problem: Fieldrunners still isn't showing up in the software center for me, but following the directions on my subscriptions page (), I was able to manually add the PPA to my software sources and install the fieldrunners package.

what PPA?

---

### Post by Dlambert on 2012-08-17
New builds have been updated/issues fixed.

---

### Post by red13 on 2012-08-17
uplink still not accepting screen resolution with out hack,fieldrunners still not in usc, also can't get it to run.

---

### Post by sffvba[e0rt on 2012-08-17
Redeemed the games for my phone... not had time to check them out yet...


404

---

### Post by era506 on 2012-08-18
Has anyone been able to download Fieldrunners from the Ubuntu Software Center? I have even updated my sources with sudo apt-get updated and restarted USC and I'm still getting "There isn&#8217;t a software package called &#8220;fieldrunners&#8221; in your current software sources." Am I missing something?

---

### Post by red13 on 2012-08-18
I checked about an hour ago and seen a i386 show up in search result but when I clicked more info I got 404.
Been playing Bit.Trip Beat since I purchased the Humble Bundle it is awsome.
disapointed with uplink and Field Runners, I hope they get the bugs sorted out would like to try them out with no need of hacking.
I am happy with purchase though because of Bit.Trip Beat, ganna play spirits next it runs fine I started all 5 to see which ones were bugged,
for me it seems only uplink and fieldrunners are bugged at the moment.

---

### Post by don draper on 2012-08-19
Hi, uplink works fine once you have changed the resolution in the games menue.

But fieldrunners 64bit doesnt work at all on my 12.04. It pops up and...

> ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM plughw:0,0
cannot open audio device (No such file or directory)
Fieldrunners: pcm.c:928: snd_pcm_state: Assertion `pcm' failed. I tried the deb package, via SC, .tar.gz, no luck.  Any ideas? They posted a new version this morning, that doesnt even install. Disappointing!

---

### Post by era506 on 2012-08-19
Well I'm still unable to redeem Fieldrunners in my Ubuntu 64 bit. The latest build from my bundle page installs but gives me this error when starting:

> /opt/fieldrunners/fieldrunners: error while loading shared libraries: libglut.so.3: wrong ELF class: ELFCLASS64

---

### Post by Skarjoko on 2012-08-19
EDIT: I'm on 12.04.

So after installing SpaceChem, I keep getting dependency issues:

```

sarim@devbox:~/Downloads$ sudo dpkg -i SpaceChem-i386.deb 
Selecting previously unselected package zachtronicsindustries-spacechem:i386.
(Reading database ... 183792 files and directories currently installed.)
Unpacking zachtronicsindustries-spacechem:i386 (from SpaceChem-i386.deb) ...
dpkg: dependency problems prevent configuration of zachtronicsindustries-spacechem:i386:
 zachtronicsindustries-spacechem:i386 depends on mono-runtime (>= 2.4).
 zachtronicsindustries-spacechem:i386 depends on libmono-wcf3.0-cil (>= 2.4).
 zachtronicsindustries-spacechem:i386 depends on libmono-winforms2.0-cil (>= 2.4).
 zachtronicsindustries-spacechem:i386 depends on xclip (>= 0.08); however:
  Package xclip:i386 is not installed.
dpkg: error processing zachtronicsindustries-spacechem:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zachtronicsindustries-spacechem:i386

```

Now I can't seem use apt-get at all without resolving the issue:

```

sarim@devbox:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 zachtronicsindustries-spacechem:i386 : Depends: libsdl1.2debian:i386 (>= 1.2) but it is not installed
                                        Depends: libsdl-image1.2:i386 (>= 1.2) but it is not installed
                                        Depends: libsdl-mixer1.2:i386 (>= 1.2) but it is not installed
                                        Depends: mono-runtime:i386 (>= 2.4) but it is not installed
                                        Depends: libmono-wcf3.0-cil:i386 (>= 2.4) but it is not installable
                                        Depends: libmono-winforms2.0-cil:i386 (>= 2.4) but it is not installable
                                        Depends: xclip:i386 (>= 0.08) but it is not installed
E: Unmet dependencies. Try using -f.

```

Doing "sudo apt-get -f install" just removes the SpaceChem package. The game works fine, however I can't use apt-get to upgrade packages anymore.

Anyone else having this issue?

---

### Post by don draper on 2012-08-20
> /opt/fieldrunners/fieldrunners: error while loading shared libraries: libglut.so.3: wrong ELF class: ELFCLASS64  Meanwhile I get the same message. I am a noob. But obviously fieldrunners wants a 32bit file and gets 64bit.

Edit: A 64bit "friendly" version will be released shortly.

Edit2: Latest build uploaded works. Solved!

---

### Post by Carborundum on 2012-08-22
Four "new" titles have been added (all which have been part of previous bundles (not that I'm complaining)): World of Goo, Osmos, Edge, and Anomaly - Warzone Earth. World of Goo is already in USC and can be redeemed immediately. The other three are not yet there; I have asked the Humble Bundle people if they know whether they will be added or not.

Edit: I just got a response from the Humble team (wow, that was fast!): 
[QUOTE="Humble Support Ninja"]Anomaly, EDGE and Osmos should all appear in the Ubuntu Software Center pretty soon.  Links will be added to them as well.[/QUOTE]

---

### Post by era506 on 2012-08-22
> **don draper said:**
> Meanwhile I get the same message. I am a noob. But obviously fieldrunners wants a 32bit file and gets 64bit.

Edit: A 64bit "friendly" version will be released shortly.

Edit2: Latest build uploaded works. Solved!

Cool! I'm downloading the new build now and will report back :p

EDIT: hey it works! I'm wondering why they don't add it to the USC...?

---

### Post by xtjacob on 2012-08-24
> **don draper said:**
> Hi, uplink works fine once you have changed the resolution in the games menue.

But fieldrunners 64bit doesnt work at all on my 12.04. It pops up and...

 I tried the deb package, via SC, .tar.gz, no luck.  Any ideas? They posted a new version this morning, that doesnt even install. Disappointing!

Did anyone find a solution to this? I'm getting the same error:```
cannot open audio device (Device or resource busy)
Fieldrunners: pcm.c:928: snd_pcm_state: Assertion `pcm' failed.
Aborted (core dumped)

```

---

### Post by Langney on 2012-08-26
Brought the humble bundle this time as I do everytime. I just felt this entry was alittle weak. Maybe I'm just getting spoilt :(

---

### Post by cor2y on 2012-08-26
Has anyone gotten fieldrunners via the USC?
The error i get is Not Found when i try to activate it for USC installation.
The other games on the USC page all installed with no problems except field runners.

---

### Post by Carborundum on 2012-08-26
> **cor2y said:**
> Has anyone gotten fieldrunners via the USC?
The error i get is Not Found when i try to activate it for USC installation.
The other games on the USC page all installed with no problems except field runners.
Yeah, Fieldrunners is behaving strangely in SC for me too. I can find it, but I can't install it because "it is not available for my current Ubuntu version". I was able to install it with ```
sudo apt-get install fieldrunners
```
after manually adding the ppa to my sources though.

---

### Post by willbe1kenobi on 2012-08-26
I bought this pack day 1 even though I already had 2 of the games (Uplink from their 'Introversion Bundle' and BIT.TRIP BEAT which I cannot remember where I got it from) but I still really enjoy each and every bundle they put together.

---

### Post by oldrocker99 on 2012-08-26
> **Langney said:**
> Brought the humble bundle this time as I do everytime. I just felt this entry was alittle weak. Maybe I'm just getting spoilt :(

There was a blog post a couple months back called, "The Incredible Shrinking Humble Bundle" which said roughly the same thing.

---

### Post by Dlambert on 2012-08-27
The game publishers have to WANT their games in the bundle first. I just can't wait till the promised trine 2 bundle comes.

---

### Post by shreepads on 2012-08-29
World of Goo downloaded via Software Centre (from the Humble Bundle link, which directed me to a Launchpad site for login, which then presented links, which in turn opened Software Centre where I clicked buy, re-entered my Launchpad creds again and then started the download and install)... Phew!

But it's working ferpectly!!

EDIT: Hmmmm spoke too soon, on running the second time the left side launcher panel continued to be displayed after launching Goo (which went fullscreen) distracting from the play experience...

---

### Post by shreepads on 2012-08-29
> **shreepads said:**
> World of Goo downloaded via Software Centre (from the Humble Bundle link, which directed me to a Launchpad site for login, which then presented links, which in turn opened Software Centre where I clicked buy, re-entered my Launchpad creds again and then started the download and install)... Phew!


Same approach for Osmos, working perfectly.. So far....

:D

---

### Post by Perfect Storm on 2012-08-29
> **shreepads said:**
> World of Goo downloaded via Software Centre (from the Humble Bundle link, which directed me to a Launchpad site for login, which then presented links, which in turn opened Software Centre where I clicked buy, re-entered my Launchpad creds again and then started the download and install)... Phew!

But it's working ferpectly!!

EDIT: Hmmmm spoke too soon, on running the second time the left side launcher panel continued to be displayed after launching Goo (which went fullscreen) distracting from the play experience...

1. Go to **/opt/world-of-goo/properties**
2. Copy **config.txt** to .WorldOfGoo in your home folder (hidden).
3. Open afterwards the copied config file with a text editor.
4. Change:

  [I]<param name="screen_width" value="**800**" />
  <param name="screen_height" value="**600**" />[/I]

So it fit your monitor resolution.

---

### Post by shreepads on 2012-08-31
> **Artificial Intelligence said:**
> 1. Go to **/opt/world-of-goo/properties**
2. Copy **config.txt** to .WorldOfGoo in your home folder (hidden).
3. Open afterwards the copied config file with a text editor.
4. Change:

  [I]<param name="screen_width" value="**800**" />
  <param name="screen_height" value="**600**" />[/I]

So it fit your monitor resolution.

Thanks, that makes it look a lot better (at 1920x1200)... But I think there is a separate underlying defect in Unity...

I was unable to reproduce that defect again (at original 800x600) despite trying several times. 

But then I got a new problem, after running Goo if I do a Lock Screen, the Lock Screen window is a small 800x600 window in the top left corner of the screen, instead of taking over the whole screen space. See attached...

---

### Post by cerda on 2012-09-01
> **shreepads said:**
> Thanks, that makes it look a lot better (at 1920x1200)... But I think there is a separate underlying defect in Unity...

I was unable to reproduce that defect again (at original 800x600) despite trying several times. 

But then I got a new problem, after running Goo if I do a Lock Screen, the Lock Screen window is a small 800x600 window in the top left corner of the screen, instead of taking over the whole screen space. See attached...

I change my resolution doing the same steps and had no problem with the lock screen. Using ubuntu 12.04 with unity and OPEN SOURCE drivers. Did you try that?

---

### Post by shreepads on 2012-09-01
> **cerda said:**
> I change my resolution doing the same steps and had no problem with the lock screen. Using ubuntu 12.04 with unity and OPEN SOURCE drivers. Did you try that?

Yes, same here, changing Goo's res makes the lock screen problem go away... 

But there still is a defect here if running games that go fullscreen at a lower res causes the lock screen to behave like that even after the desktop is restored to full res once the game is over...

Re open source drivers, going a little OT, but they are no good for my setup and am using the propriatary NVidia drivers from the repositories.. Have documented in detail here

[http://ubuntuforums.org/showthread.php?t=1971029](http://ubuntuforums.org/showthread.php?t=1971029)

And filed a Launchpad bug here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907)

---

### Post by shreepads on 2012-09-02
Fieldrunners still not in Ubuntu Software Centre..

Downloaded 64 bit .deb (fieldrunners_1.0.0-4_64bit.deb) from the Humble Bundle site and installed.

Working fine, though I guess I won't get any updates automatically.

Running in windowed more, which is fine, but anyone know how to change res (not available in in-game options)?

---

### Post by contributor on 2012-09-13
When I got uplink in the HumbleBundle, an error message "The Screen size is too small" continuously popping up. 
My tablet is 7", I can see the game loading in the background with sound/animation all working.

---

### Post by shreepads on 2012-09-26
> **shreepads said:**
> Fieldrunners still not in Ubuntu Software Centre..

Downloaded 64 bit .deb (fieldrunners_1.0.0-4_64bit.deb) from the Humble Bundle site and installed.

Working fine, though I guess I won't get any updates automatically.

Running in windowed more, which is fine, but anyone know how to change res (not available in in-game options)?

Tried to install same FieldRunners .deb in Lucid 10.04.4 but got a package version dependency error on libasound2:

> Error: Dependency is not satisfiable: libasound2 (>= 1.0.23)

Tried force install via command line

```
$ sudo dpkg -i --force-depends-version fieldrunners_1.0.0-4_64bit.deb
```

Installed fine (while reporting package version mismatch).

While running sound was garbled (as expected) and gameplay was much faster then expected. But it also broke Update Manager so 'Removed Completely' from Synaptic (which identified it quite handily as a broken package)..

I do wish the Humble Bundle system requirements page for Linux would specify such things in more detail..

---

