---
title: "Second Guessing NVIDIA GeForce 5500 Install"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by mstrkrft on 2008-01-04
Hi,

Ok, so I have gotten my PCI 256mb Geforce FX 5500 to load up (using the various tutorials in the forums - blacklisting agp slots, installing drivers via envy, and editing the xorg.conf file).  The computer is running fine and great, but the other day I looked at the "Appearance" options and began to second guess that Ubuntu was actually using the Nvidia card.  It looks fine, don't get me wrong, I am running a 1600X1050 widescreen with some desktop effects, but I just want to be sure that it is not using the onboard card anymore - I want to be suing the nvidia card to its full potential.

Under the "graphics cards" tab - 2 cards are listed: the first is the onboard Intel, and the second is the "nvidia".  In my BIOS settings I only have 2 options (that I can find) for my video - either "onboard" or "auto".  I have it set to "auto" and my monitor is plugged into the card and not the onboard.

Is there anything I can do or any command I can run to determine if the nvidia card is being used as the primary source for video memory/how much video memory I have?

Thanks.

---

### Post by PmDematagoda on 2008-01-04
Could you post the result of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by mstrkrft on 2008-01-04
I certainly will.  Unfortunately I am at work (XP...), but I will post results when I get home.  Thanks!

---

### Post by AnonCat on 2008-01-04
If you've blacklisted the agpslots "blacklist intel_agp, blacklist agpgart" and the xorg.conf file says you're using "nvidia" or "nv" as the driver, you're definitely using the 5500 card.  Try hooking your monitor into your onboard video and see if Ubuntu boots up.  If it doesn't or acts strange then you can be at peace that your 5500 is being utilized.

---

### Post by FuturePilot on 2008-01-04
Start the Nvidia settings
```
nvidia-settings
```
If you're using any driver other than the Nvidia driver it will give you an error. If there's no error you're probably fine.

---

### Post by mstrkrft on 2008-01-04
i have blacklisted both agpgart and intel_agp and added nvidia to xorg.conf, monitor does not work when plugged into onboard.  I will still post info when i get home.

I guess it would just be satisfying to run some sort of command and look at some option that says:

card: nvidia
memory: 256 MB

still new to ubuntu and just used to the way XP displays info

Thanks for your quick replies:)

---

### Post by FuturePilot on 2008-01-04
> **mstrkrft said:**
> i have blacklisted both agpgart and intel_agp and added nvidia to xorg.conf, monitor does not work when plugged into onboard.  I will still post info when i get home.

I guess it would just be satisfying to run some sort of command and look at some option that says:

card: nvidia
memory: 256 MB

still new to ubuntu and just used to the way XP displays info

Thanks for your quick replies:)

The Nvidia settings control panel will tell you this information.
Also if you enter 
```
glxinfo
``` in the terminal look at the first few lines. If you see something like this you should be fine
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation

```

---

### Post by mstrkrft on 2008-01-04
Thanks everyone.  FuturePilot: Nvidia settings (also shows up in "Applications > System Tools > Nvidia Settings") gave me all the info I need.  My card is up and running

---

