---
title: "Issue with Flash Player and fonts"
date: 2005-12-01
forum: Desktop Environments
---

### Post by shadow07 on 2005-12-01
I have been having problems with the Flash player.  I cannot for the life of me get certain sites to display text within the flash object.  Nor, if I go to edit the Flash Player properties, there's no text.

I have tried using the Macromedia tarball, as well as the flashplayer-mozilla package.

Has anyone ever seen this problem or can provide a fix?  I am running Firefox 1.5, the official release.

---

### Post by shadow07 on 2005-12-02
Anyone?!?!?

---

### Post by likenoother on 2005-12-02
[QUOTE=shadow07]I have been having problems with the Flash player.  I cannot for the life of me get certain sites to display text within the flash object.  Nor, if I go to edit the Flash Player properties, there's no text.

I have tried using the Macromedia tarball, as well as the flashplayer-mozilla package.

Has anyone ever seen this problem or can provide a fix?  I am running Firefox 1.5, the official release.[/QUOTE]

I had the same problem. Everything was sorted out by installing the Mozilla Flash plugin via Synaptic. I think you have to delete first the one in the .plugins directory and then to install the right package.

take care
likenoother

---

### Post by cbudden on 2005-12-02
I have this problem aswell.

---

### Post by Hairy_Palms on 2005-12-02
i fixed this problem by installing flash through firefox itself, remove all flash plugins then go to a site with flash and you can get it to set itself up perfectly.

---

### Post by cbudden on 2005-12-02
Ok, I re installed but still get no text on the settings box.

---

### Post by mrmcctt on 2005-12-02
I have basically the same issue.  I can go to my Road Runner homepage without Flash Plugins installed and I can see all the text.  Install the plugin and when I navigate to the Road Runner site, all the navigation buttons on the left side of the screen are blank.  By blank I mean I can see them, they function but there is no text in them.  If I uninstall the Flash Plugin again, I can see the button text again but cannot login to the site.

Maybe someone else could look at this?  The link is [www.rr.com](www.rr.com).  You will probably come to a site requesting state and provider.  You can select Texas for the state and Heart of Texas for the provider and it should then take you to the site.

Thanks

---

### Post by mrmcctt on 2005-12-02
By the way, the link I supplied above is nothing nasty.  

I attached a screenshot.

---

### Post by dcstar on 2005-12-02
[QUOTE=mrmcctt]I have basically the same issue.  I can go to my Road Runner homepage without Flash Plugins installed and I can see all the text.  Install the plugin and when I navigate to the Road Runner site, all the navigation buttons on the left side of the screen are blank.  By blank I mean I can see them, they function but there is no text in them.  If I uninstall the Flash Plugin again, I can see the button text again but cannot login to the site.

Maybe someone else could look at this?  The link is [www.rr.com](www.rr.com).  You will probably come to a site requesting state and provider.  You can select Texas for the state and Heart of Texas for the provider and it should then take you to the site.

Thanks[/QUOTE]
I've just gone there and it all looks fine on my FF 1.07.

I do have the **msttcorefonts** installed on my system, so any Microsoft fonts that this particular web page may be set up for are available, do both of you having problems have these fonts installed?

---

### Post by mrmcctt on 2005-12-02
I ran the "Automatix" program and as far as I know the msttcorefonts installed.  Maybe they're in the wrong place or something.  

I've verified that it's only in Ubuntu that this happens so that may very well be the problem.  I'll have to find out where they need to be and what links need to be made.

Thanks for looking, though.  I do appreciate it.

---

### Post by mgmiller on 2005-12-02
I do not have the msttcorefonts installed and the page displays perfectly in FF 1.0.7.  The only flash listed in my about:config is:
    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

I'm pretty sure I installed it from Synaptic.  I have flashplayer-mozilla 7.0.25-0.0ubuntu1
and also:
libswfdec0.3 version 0.3.4-3ubuntu1

hope this helps

---

### Post by shadow07 on 2005-12-08
Yeah, I have the same packages installed with the same versions.

I just cannot seem to figure this problem out.  It is quite annoying.

---

### Post by benbalbo on 2005-12-08
I had the same problem, just [found this through google](http://ubuntu.wordpress.com/2005/09/17/flash-text-fix/), and it works fine for me now:

> The solution is to install gsfonts-x11 and msttcorefonts by doing:
$ sudo apt-get install gsfonts-x11 msttcorefonts

---

### Post by sbaush on 2005-12-13
[QUOTE=benbalbo]I had the same problem, just [found this through google](http://ubuntu.wordpress.com/2005/09/17/flash-text-fix/), and it works fine for me now:[/QUOTE]

Yes, it works perfectly...:KS :KS

---

### Post by mcduck on 2005-12-14
I'm suffering from the same problem,  but I already have both font packages installed. I also tried to reinstall flash plugin, but that didn't help either :/

---

### Post by shadow07 on 2005-12-18
Well, there appears to be a conflict somehere with ATI drivers and utilizing Flash.  Someone mentioned to me that the xorg.conf file was missing the correct paths to the fonts directories.  I tried adding them, but then X wouldn't start.

I'm wondering of those that are experiencing this similar issue, if you have ATI cards.  And if so, are you using the proprietary ATI driver or the Mesa driver?

---

### Post by mcduck on 2005-12-19
I have Ati card, and I'm using proprietary drivers..  I guess I'll have to take a look at those font paths..

---

### Post by shadow07 on 2005-12-19
@mcduck:

Can you please run fglrxinfo from a command prompt and post the output here?

---

### Post by slim_chiply on 2005-12-20
I struggled with problem for quite some time.  I finally solved it by adding the following to my xorg.conf:

	FontPath		"/usr/share/X11/fonts/misc"
	FontPath		"/usr/share/X11/fonts/cyrillic"
	FontPath		"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath		"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath		"/usr/share/X11/fonts/Type1"
	FontPath		"/usr/share/X11/fonts/CID"
	FontPath		"/usr/share/X11/fonts/100dpi"
	FontPath		"/usr/share/X11/fonts/75dpi"
    # paths to defoma fonts
	FontPath		"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath		"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
	FontPath		"/usr/share/fonts/truetype/msttcorefonts"

The issue is that the flgrxconf (or whatever it is called) comments out all of the font paths.

Hope this helps someone.

---

### Post by mrmcctt on 2005-12-21
Could the fact that I have the 'ati' driver and not the fglxr driver installed cause this?

I was looking at my /etc/X11/xorg.conf and noted that the lines from the previous post were in my xorg.conf but that I am running the 'ati' driver and not the fglrx driver.  My laptop has an ATI Mobility Radeon 9000 graphics chip installed.

---

### Post by mcduck on 2005-12-21
[QUOTE=shadow07]@mcduck:

Can you please run fglrxinfo from a command prompt and post the output here?[/QUOTE]Sure, here it is:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```

slim_chiply:
That worked, thanks.

---

### Post by shadow07 on 2005-12-22
@mcduck:

We are running the exact same ATI driver.  I'm glad that someone else has been expereincing the same issue I was.

@slim_chiply:

THANK YOU!!!!!!!!  Finally have the biggest issue I have been tackling for the past 2 months.

---

