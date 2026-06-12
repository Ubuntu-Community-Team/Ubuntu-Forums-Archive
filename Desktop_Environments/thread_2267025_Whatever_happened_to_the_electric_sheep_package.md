---
title: "Whatever happened to the electric sheep package?"
date: 2015-02-26
forum: Desktop Environments
---

### Post by Monsuco on 2015-02-26
I used to always use the electric sheep package to set my screensaver and I still use it as my screensaver on Windows. I liked the fractals it generated. I decided to try going back to it but it's no longer in the repositories for some reason. I tried to compile from source but the instructions I found online failed. 

Is there a PPA or third party repo that maintains current versions of Electric Sheep for 14.10?

Thus far I've managed to install a very old .deb from an old version of Ubuntu but it'd be nice to have a version that wasn't this ancient. For starters it seems to have trouble with my netbook's graphics card and I suspect an updated version of the program might behave itself a tad better.

Also I put this under Desktop Environments simply because this relates to screensavers, themes, etc. I generally use Kubuntu on my lappy and Lubuntu on my netbook but it shouldn't matter.

---

### Post by v3.xx on 2015-02-26
Found this

[http://ubuntuforums.org/showthread.php?t=2223173](http://ubuntuforums.org/showthread.php?t=2223173)

---

### Post by Monsuco on 2015-02-27
I've seen that thread actually. The problem is that version of electric sheep is really really obsolete. Are there no .deb packages of reasonably current versions?

---

### Post by Monsuco on 2015-02-27
Okay, on my KDE system I have the really old .deb installed but I can't seem to get it to show up as an option in the kscreensaver settings.

---

### Post by Monsuco on 2015-02-27
I'm trying to build the program from source but make is having issues.

```

Makefile:1006: recipe for target 'ContentDecoder.o' failed
make[1]: *** [ContentDecoder.o] Error 1
make[1]: Leaving directory '/home/monsuco/Downloads/electricsheep-read-only/client_generic/Client'
Makefile:501: recipe for target 'all-recursive' failed
make: *** [all-recursive] Error 1

```

Any ideas?

---

### Post by mc4man on 2015-02-27
Which source?

---

### Post by Monsuco on 2015-02-27
That's what you get at the end of the make process. I got the sources from subversion just like all the guides say.

---

### Post by Monsuco on 2015-03-02
Hmm, I've *sorta* got it working. Basically what you can do is install the electricsheep deb package and dependencies [from here]("http://ubuntuforums.org/showthread.php?t=2223173&p=13111728#post13111728") with dpkg. Then you need to do a little work. 

For Kubuntu I need to configure it to work with kscreensaver. Here's how I managed to get that to work.

As root cd to /usr/share/kde4/services/ScreenSavers/

Use nano or another editor to create the following file.

```

[Desktop Entry]
Name=Electric Sheep
Exec=electricsheep
Icon=preferences-desktop-screensaver
Type=Service
X-KDE-ServiceTypes=ScreenSaver
Actions=InWindow;Root;Setup;

[Desktop Action InWindow]
Exec=electricsheep -window-id %w
Name=Display in specified window
NoDisplay=true

[Desktop Action Root]
Exec=electricsheep -window-id %w
Name=Display in root window
NoDisplay=true

[Desktop Action Setup]
Name=Display setup dialog
Exec=electricsheep-setup
Icon=kscreensaver

```


Save it as electricsheep.desktop

Keep your terminal open. cd to /var/lib/dpkg/info/ and use nano to edit the file kscreensaver.list

Add the line /usr/share/kde4/services/ScreenSavers/electricsheep.desktop to where it has a list to the launchers of other screensavers.

Run the command electricsheep-preferences to configure electric sheep. I've had better luck with setting the driver to gl or gl3. 

It seems electricsheep may be outputting videos using mplayer. For some reason though, it has overscan issues with my computers.

[ATTACH=CONFIG]260400[/ATTACH]

It does this on my Lubuntu netbook too. I wonder why? There's bound to be something I could do to tell it to scale the image to fit the display.

I have scoured the web looking for reasonably modern versions of a .deb of electricsheep but I've come up with nothing. I suspect part of the reason why Ubuntu isn't packaging it anymore is that [it doesn't appear to be in the developmental repositories for Debian]("https://packages.qa.debian.org/e/electricsheep.html") anymore either. It's still available for Wheezy but not for Jessie, Sid or experimental.

Oh well, fun little project even if it only sorta works.

---

### Post by ichthyo on 2015-08-09
> **Monsuco said:**
> I used to always use the electric sheep package....
I decided to try going back to it but it's no longer in the repositories for some reason.

Is there a PPA or third party repo that maintains current versions of Electric Sheep for 14.10?



Hello Monsuco and the others,

here is what the world needs right now: a **new ElectricSheep package** for Debian, Ubuntu and similar flavours.


It is based on the current source tree as found in Git (2015-07-18)

The Debian packaging is somewhat based on the old debian package, but since the upstream source
has been remoulded, I've also streamlined and simplified the package definition and adjusted all the build dependencies.

For now I've made packages for Ubuntu Trusty (LTS) and Vivid. Hope that helps

[B]ppa:ichthyo/zeug
[https://launchpad.net/~ichthyo/+archive/ubuntu/zeug](https://launchpad.net/~ichthyo/+archive/ubuntu/zeug)


have fun with your sheep
-- Ichthyo

PS[/B]: in case anyone is interested in the Package definition as such,
please see my Git repo: [https://github.com/Ichthyostega/electricsheep](https://github.com/Ichthyostega/electricsheep)
Git clone URL: [https://github.com/Ichthyostega/electricsheep.git](https://github.com/Ichthyostega/electricsheep.git)

---

### Post by evaarties on 2015-09-21
Good job Ichthyo. It works great in 15.04. Maybe you can contact [https://twitter.com/ELECTRICSHE3P](https://twitter.com/ELECTRICSHE3P) to have your changes merged with there code and update [http://electricsheep.org/node/51](http://electricsheep.org/node/51) ?

---

### Post by spot-draves on 2015-09-22
Many Thanks! I updated [http://electricsheep.org/node/51](http://electricsheep.org/node/51)

---

### Post by Helven Ink on 2015-12-02
Ichtyo, Thank you SO much!

Has anyone figured out how to set it up as a screen-saver again? Or do I just have to keep running it manually when I want?

---

