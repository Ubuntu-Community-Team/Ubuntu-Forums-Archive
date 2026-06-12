---
title: "Dual-head Compiz on ATI Radeon 9700 causes strange desktop rendering bug"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by sickpuppet on 2007-06-16
Hi - 

I'm running Feisty with all the latest updates. I've enabled all desktop effects on Compiz (System->Preferences->Desktop EFfects) and I've set up a dual-head display simply by adding the following snippet between the comments to the 'Device' section of my xorg.conf:

```

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
        Driver          "ati"
        BusID           "PCI:3:0:0"
        # Added for dual-head
        Option  "MonitorLayout"                 "LCD, CRT"
        Option  "CRT2Position"                  "RightOf"
        Option  "MetaModes"                     "1280x1024-1280x1024"
        Option  "MergedXinerama"                "on"
        Option  "MergedNonRectangular"          "true"
        Option  "MergedFB"                      "true"
        # End of dual-head config

```

There's now a chunk of my desktop that doesn't render properly - windows leave 'ghost' trails in that part. Take a look at this screenshot:

[[IMG]http://www.ir52.org/images/miniScreenshot.png[/IMG]]("http://www.ir52.org/images/Screenshot.png")

What's going on, and how do I fix it?

regards
Ben

---

### Post by sickpuppet on 2007-06-18
Bump -any ideas?

---

### Post by kpolice on 2007-06-18
Your card has a max texture size of 2048x2048 so anything beyond that won't work.

Now you have 2560 pixels wide and that's the reason why it doesn't work. At least that was what some of the developers told me when I tried to run a dual screen setup.

---

### Post by sickpuppet on 2007-06-18
Hi kpolice - 

Interesting! Thanks for your response. Did you buy a replacement card, and if so, which one? Note that my dual head Windows XP setup is perfect at the same resolution.

Did you get in touch with the Compiz developers?

regards
Ben

---

### Post by kpolice on 2007-06-18
No I didn't buy a new one because I have a notebook :P .

---

### Post by sickpuppet on 2007-06-18
OK, so with a bit of experimentation I've discovered that it's Compiz causing the problem - it goes away as soon as I disable 'Desktop Effects'. Ought to have tried that first, I guess, before posting here!

[URL="http://www.ir52.org/images/Screenshot2.png"]
[IMG]http://www.ir52.org/images/miniScreenshot2.png[/IMG][/URL]

I'll try Beryl and see if it's any better behaved than Compiz... seems to have a stack more eye-candy. :-)

Ubuntu is the Windows-killer for me... Thanks again to kpolice for the response.

cheers
Ben

---

### Post by kpolice on 2007-06-18
You will get the same with beryl, I tried both and got the same results. 

The problem is that the both use 1 single texture to represent your desktop and you don't get the bug without Compiz/Beryl or with WinXP because it actually isn't accelerated by your card.

---

