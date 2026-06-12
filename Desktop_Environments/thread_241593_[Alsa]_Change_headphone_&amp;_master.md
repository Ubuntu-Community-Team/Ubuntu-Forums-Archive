---
title: "[Alsa] Change headphone &amp; master"
date: 2006-08-22
forum: Desktop Environments
---

### Post by l_b on 2006-08-22
Hi,

There's something wrong with my alsa settings. Somehow, the master and headphone settings are changed. This have always been the problem (at least with ubuntu). How can I change the two with alsa? In what file can I find this settings?

Thanks in advance!

---

### Post by cptjaben on 2006-08-22
Sorry if this isn't the problem your having, i wasn't exactly sure what you meant when you said your alsa settings were changed. In the case that your master and headphone settings are changed in regards to volume, you can use alsamixer to change volume related settings. To start alsamixer just type the program name at the command prompt. You can move between the virtual faders using the left and right arrow keys. The screen scrolls at the left and right-hand side to display additional virtual faders. To increase or decrease the volume levels, use the up and down arrow keys. I hope this helps

---

### Post by l_b on 2006-08-22
Sorry if I was not clear. I mean that I use my headphone control as master control. And the master control doesn't do anything. So it looks likes they are switched in behaviour.

---

### Post by tontonsalam on 2006-10-29
I have exactly the same problem... 
even when I installed edgy...

---

### Post by antealin on 2006-11-06
This problem showed up for me when I upgraded to edgy.

---

### Post by weel on 2006-11-13
The poster probably meant to say the two volume controls were *swapped*, or, more generally, *mixed up*. I think I am stuck here with the same issue. On my machine (I'm running kubuntu 6.10 on an IBM Thinkcentre with a cheapish Intel sound chip of which I don't remember the serial number right now), the headphone channel in kmix controls the output volume to the one and only audio output jack (there is no separate headphone jack on this machine), and the master channel doesn't do anything. This is probably a bug that just needs to be fixed, but it would be nice to find a workaround, given that the master channel is the only one that I can assign global shortcut keys for.

---

### Post by cyberscribe on 2008-06-03
I also have this problem - on hardy.  The" Master" slider  does nothing at all: enabling or disabling, raising or lowering it has no effect on either the external speaker volume or the headphone volume.

The "Headphone" slider, however, works for both external speakers and the headphones.  Setting it to "disabled" turns off volume to both external speakers and headphones.

Any fixes for this problem yet?

---

