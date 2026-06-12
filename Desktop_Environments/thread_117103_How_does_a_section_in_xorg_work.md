---
title: "How does a section in xorg work"
date: 2006-01-14
forum: Desktop Environments
---

### Post by djgenesis on 2006-01-14
I was going through howtos on how to change the refresh rate on my screen along with my resolution and it all comes down to two sections.
```

Section "Monitor"
	Identifier	"Monitor 0"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

```

and 

```

 Subsection "Display"
        Depth       24
        Modes       "1024x768" "1280x1024" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

```


But no one explained what they do. 
I was on hoary with a 1280x1024 screen and i changed the first mode in the "display" section to 1024x768 (Yes, i lost my glasses and now i am a bit blind :( ) anyway.

Now the gdm starts ok, and the resolution is 1024x768 BUT the desktop is bigger than my resolution and now i have to scroll up and down to get around my windows. 

So i figured there is something that i am missing.

Can anyone explain what these vaules actually do ? What is this Horizsync and vertrefresh options? And why is this screen resolution happening to my little box? 

Cheers all 
genxx

---

### Post by bernardfrancois on 2006-01-18
Probably you have to change the screen resolution under **system > preferences > screen resolution**
It might be set at 1280x... while your display is showing 1024x..., which causes the scrolling effect.

You can also try the different modes using CTRL+ALT+'+' (plus), and CTRL+ALT+'-' (minus).

Horzsync is the horizontal sync rate of your display (I dunno exactly what it means)
Vertrefresh is the vertical refresh rate in Hz (how many times the electron bundle of your screen goes up and down in one second - if you have a CRT... don't try to count it :d)

You can find those parameters in your display's manual or on the site of the manufacturer.

Open a shell and execute **man xorg.conf** to get more information about all the details of the xorg.conf file.

---

