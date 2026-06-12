---
title: "need help making desktop look like OSX"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by tech9 on 2007-12-12
Hi All,

 After seeing many others desktop/OS customizations; I am trying to make my desktop look exactly like OSX. I followed Dark Star's tutorial: I was able to install the theme, but did not succeed with creating  the docking bar with all if the animated icons - like OSX has. Also, I was not able to download and install icon set from Dark Star's tutorial either. Does anyone have any more advice, or could list the steps that I need to execute to create the OSX docking bar at the bottom of the screen?

Thanks,

T9

---

### Post by rune0077 on 2007-12-12
Depends on what docking bar you want. If you want Avant Windows Navigator, there's a guide somewhere on the forum on how to install it. Search for AWN and I'm sure it'll come up.

---

### Post by tech9 on 2007-12-12
> **rune0077 said:**
> Depends on what docking bar you want. If you want Avant Windows Navigator, there's a guide somewhere on the forum on how to install it. Search for AWN and I'm sure it'll come up.

Hey Thanks rune0077!

---

### Post by rune0077 on 2007-12-12
No prob. See, I can be helpful too :)

---

### Post by adityakavoor on 2007-12-12
u shud try mac4lin

clik [here]("http://sourceforge.net/projects/mac4lin")

---

### Post by tech9 on 2007-12-12
> **rune0077 said:**
> No prob. See, I can be helpful too :)

I see :) 
sorry for the insults in the backyard, I will delete the comments... I stay out of the backyard these days. It gets me in trouble.

---

### Post by tech9 on 2007-12-12
> **adityakavoor said:**
> u shud try mac4lin

clik [here]("http://sourceforge.net/projects/mac4lin")


Thanks [adityakavoor]("http://ubuntuforums.org/member.php?u=270146") I will check it out! :)

---

### Post by rune0077 on 2007-12-12
> **tech9 said:**
> I see :) 
sorry for the insults in the backyard

Yeah me to. My motto: "What goes on in The Backyard stays in The Backyard".

---

### Post by tech9 on 2007-12-12
> **rune0077 said:**
> Yeah me to. My motto: "What goes on in The Backyard stays in The Backyard".

good motto! :)

BTW - AWN is cool!

Happy Holidays!

---

### Post by tech9 on 2007-12-12
AWN will not autostart upon loading the OS, even when I copied the icon in /usr/share/autostart.... any ideas?

---

### Post by JordanII on 2007-12-12
Leopard or Tiger? If Leopard try Mac4Lin.

---

### Post by rune0077 on 2007-12-12
> **tech9 said:**
> AWN will not autostart upon loading the OS, even when I copied the icon in /usr/share/autostart.... any ideas?

You can add it in System > Preferences > Sessions.

In the Startup tab, add a new entry, call it whatever you want, and under command type "avant-window-navigator" (minus the quotes). Then click the Session tab and hit Save Session (or whatever it's called). Dunno, but that did it for me (you probably should remember to delete the file you already put in autostart first).

---

### Post by tech9 on 2007-12-13
> **JordanII said:**
> Leopard or Tiger? If Leopard try Mac4Lin. I looked into that site... it looks like the download said 1.3 TB - That's huge

---

### Post by tech9 on 2007-12-13
> **rune0077 said:**
> You can add it in System > Preferences > Sessions.

In the Startup tab, add a new entry, call it whatever you want, and under command type "avant-window-navigator" (minus the quotes). Then click the Session tab and hit Save Session (or whatever it's called). Dunno, but that did it for me (you probably should remember to delete the file you already put in autostart first).

worked like a charm - Thanks again rune0077. Normally, I would just load icons in the autostart directory and I would be on my way, but for whatever reason... it didn't work.

Also have you noticed issues or bugs with AWN when setting it up for auto-hide when it's not being used? Sometimes the dock will not show after I hover over the bottom of the menu.

---

### Post by rune0077 on 2007-12-13
> **tech9 said:**
> 
Also have you noticed issues or bugs with AWN when setting it up for auto-hide when it's not being used? Sometimes the dock will not show after I hover over the bottom of the menu.

Yeah, AWN is still "in development", meaning it's not entirely stable. It behaves funny sometimes, and certain things will make it crash. Good thing is, the developers seem pretty active, so make sure to check for updates periodically.

---

### Post by tech9 on 2007-12-13
> **rune0077 said:**
> Yeah, AWN is still "in development", meaning it's not entirely stable. It behaves funny sometimes, and certain things will make it crash. Good thing is, the developers seem pretty active, so make sure to check for updates periodically.

Yeah, I saw some other posts regarding this. I also heard that AWN will be included in Hardy Heron. Well, hopefully by then all the bugs will be worked out.

---

### Post by gatoz on 2007-12-13
AWN is still a beta, I don't think there is an autostart, but they should include one soon.

---

### Post by voteforpedro36 on 2007-12-13
When running on my computer, it just randomnly killed itself. Once I figured out it was just hiding, I tried to figure out how to add launchers to it. Yeah they never worked...

If you want a different bar, there's kiba-dock (there's a guide somewhere around here), or install gDesklets, and do one from there (for me it was most stable...)

---

### Post by tech9 on 2007-12-14
> **voteforpedro36 said:**
> When running on my computer, it just randomnly killed itself. Once I figured out it was just hiding, I tried to figure out how to add launchers to it. Yeah they never worked...

If you want a different bar, there's kiba-dock (there's a guide somewhere around here), or install gDesklets, and do one from there (for me it was most stable...)

Thanks, but I got AWN working perfectly now. 
What kind of problems are you having with launching apps? I was able to setup all mine with no problem.

---

### Post by tech9 on 2007-12-14
> **gatoz said:**
> AWN is still a beta, I don't think there is an autostart, but they should include one soon.

I am sure they will give you an option to autostart in HH

---

