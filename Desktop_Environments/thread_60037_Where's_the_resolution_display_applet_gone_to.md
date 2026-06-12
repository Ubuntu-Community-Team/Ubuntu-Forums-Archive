---
title: "Where's the resolution display applet gone to?"
date: 2005-08-26
forum: Desktop Environments
---

### Post by aftertaf on 2005-08-26
Hi all....

New to Ubuntu, after 2 years breaking debian regularly, decided to take it the easier way  :razz: 

I have a question, and would help an annoyance i have with linux since i started with it.
My particular pb right now is the screen resolution applet. I don't have one!!
I have searched in the options, searched on google, searched thru synaptic... no joy!

Hoary on a laptop, max res 800x600, and some control center windows are just too big for this res. Which means I can't click OK or Apply as they aren't visible.
I got round it by going to 1024*768 virtual, but with a touchpad it can end up going all over the place...
Simple solution would be to change the res when needed to see the buttons, then change back to 800*600 when finished...
hence my  ](*,) 
Can anybody help?
cheers in advance :)

---

### Post by GeneralZod on 2005-08-26
Not sure if this helps, but KDE's screen resolution "applet" (which lives in the system tray) is called "krandr".

---

### Post by aftertaf on 2005-08-26
[QUOTE=GeneralZod]Not sure if this helps, but KDE's screen resolution "applet" (which lives in the system tray) is called "krandr".[/QUOTE]
 Cheers..

I had checked in the system tray and it only gives me the battery icon and the sound icon. I just can't see the resolution thingy anywhere.
as soon as my dist-upgrade has finished i'll dblcheck in synaptic if it is installed (is it installed by default with kubuntu?)

aha!!!
apt-cache search krandr comes up blank.

searching on apt-get.org comes up blank too.

i reread what you said and understood a bit better...
just typed in krandr in root terminal and it said eh??

used autocomplete and found krandrtray - aha i thought!!
typed it, got some DCOPClient errors, then sth about ksycoca, then the icon appeared in the system tray

i'll see if it remains on reboot, but cheers a lot mate ;-) \\:D/

---

### Post by daller on 2005-08-26
If it does not open i the systemtray, simply add a shortcut in "$HOME/.kde/Autostart"

about the resolution change - is it in a specific application?

I have troubles viewing movies, cause the nv-driver stinks (Has to be GPL :))

Well, the command I use, look like this:

xrandr -s 2;APPLICATION;xrandr -s 0

What it does, is that it changes the resolution to "2" (run "xrandr" in a terminal - and you will know what I mean :))

Then it runs APPLICATION, and when APPLICATION is terminated, is changes the resolution to "0" - Quite simple (2 and 0 are system specific! check "xrandr")

---

### Post by riskbreaker927 on 2005-09-03
I have this problem too, and when I tried using KRandR it does make the system tray thing show up, but right clicking on it still does not allow me to change resolution (it says "Required X extension not available, presumably where the resolution option would be.)

---

