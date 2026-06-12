---
title: "Ubuntu 8.04 performance tweaks info request"
date: 2009-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bitterwhiteguy on 2009-08-28
Greetings all.  I've just snagged my Mini w/ Ubuntu loaded onto it and I'm looking for some tips on performance tweaks to speed up/streamline the device.  I've been a *nix end-user for awhile but never admined a box before so I'm being fairly cautious in what I roll out as far as config changes, but I'm open to suggestions.  I'm willing to put performance ahead of battery life as the ocassions when the netbook will be without AC power for mroe than a couple of hours will be infrequent.  I dug through the Wiki some and am trolling around the net for performance tweaks, but this seemed like as good a place as any to ask for suggestions.  If I missed a post in one of the stickies that deals with this area, feel free to slap me around. :)

Thanks in advance.

---

### Post by snowpine on 2009-08-28
Which model of Dell Mini do you have? The 9/10v have different graphics chips from the 10/12, so my advice will be different depending...

---

### Post by Bitterwhiteguy on 2009-08-28
> **snowpine said:**
> Which model of Dell Mini do you have? The 9/10v have different graphics chips from the 10/12, so my advice will be different depending...

[FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]Inspiron Mini 10[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]Intel&#174;Atom&#174;Processor Z520 (1.33GHz/533MHz FSB/512K Cache)[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]1GB DDR2 SDRAM[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]10.1"  HD Widescreen Display (1366x768)[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]Intel&#174;Graphics Media Accelerator 500[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]250GB, 2.5inch, 5400RPM SATA Hard Drive[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]Non-WWAN Base, WLAN Antenna, 1GB[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]Ice Blue[/COLOR][/SIZE][/FONT]
                                                               [FONT=arial][SIZE=2][COLOR=#003366]**1**[/COLOR][/SIZE][/FONT]                                                                 [FONT=arial][SIZE=2][COLOR=#003366]UBUNTU 8.04 (Standard Edition)[/COLOR][/SIZE][/FONT]

---

### Post by snowpine on 2009-08-28
That's too bad; I have the Mini 9 (which has a different chipset) so my tweaks won't be any use to you. :( Good luck!

---

### Post by Bitterwhiteguy on 2009-08-28
> **snowpine said:**
> That's too bad; I have the Mini 9 (which has a different chipset) so my tweaks won't be any use to you. :( Good luck!

Are there any commonalities between the two that could be used to speed up things like HD access, CPU throttling, etc.?

---

### Post by snowpine on 2009-08-28
> **Bitterwhiteguy said:**
> Are there any commonalities between the two that could be used to speed up things like HD access, CPU throttling, etc.?

The Atom doesn't support CPU throttling as far as I know, and my Mini 9 doesn't have a HDD, so I don't want to give you bad advice that won't apply to your hardware. :) Lots of other Dell users here, though, and then there's this forum: [http://www.mydellmini.com/forum/](http://www.mydellmini.com/forum/)

Good luck! :)

---

### Post by Greyed on 2009-08-29
I've got a 10v so not much help here.  However the one thing I could suggest is to check to see if they enabled swap on your machine.  Mine was shipped with swap turned off (concession for SSD models?).  One of the first things I did was create a swap file and toss that into fstab.

---

