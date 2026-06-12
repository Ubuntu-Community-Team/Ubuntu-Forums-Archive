---
title: "newbie titlebar question"
date: 2009-04-16
forum: General Help
---

### Post by ac13 on 2009-04-16
When I maximize any window in ubuntu the the colored window titlebar disappears an with it the oh so important minimize, maximize and close buttons.
How can I get ubuntu to show the titlebar in maximize mode?
I am an all time windows user and I am used to have those buttons at all times.

Thanks :)

---

### Post by prem1er on 2009-04-16
They might not be disappearing your resolution might be set wrong and they are extending past the viewable screen.  Can you see your entire desktop when all windows are closed? Or is some of it being cut off?

---

### Post by ac13 on 2009-04-16
Oh my... That why I had a ton of missing files on the desktop.
My resolution is 1280x1024 and if I switch to 800x600 the desktop height is still somethink like twice as long as it should be.

Thanks for the tip, how can I fix this?

---

### Post by ncmncm on 2009-04-16
I had the same problem. I changed the theme ( System->Preferences->Appearance ) to something else and I got back the window buttons.

---

### Post by Daisuke_Aramaki on 2009-04-16
> **ac13 said:**
> Oh my... That why I had a ton of missing files on the desktop.
My resolution is 1280x1024 and if I switch to 800x600 the desktop height is still somethink like twice as long as it should be.

Thanks for the tip, how can I fix this?

Looks like the resolution is screwed up. So your computer is capable of 1280x1024, but you get a resolution lesser than that? Am i correct? Could be agraphic card driver issue. Did you look up what resolution is actually available to you right now, and what graphic card you have and such?

---

### Post by ac13 on 2009-04-16
> **ncmncm said:**
> I had the same problem. I changed the theme ( System->Preferences->Appearance ) to something else and I got back the window buttons.

unforunately that didn't do it for me :(

---

### Post by ac13 on 2009-04-16
> **Daisuke_Aramaki said:**
> Looks like the resolution is screwed up. So your computer is capable of 1280x1024, but you get a resolution lesser than that? Am i correct? Could be agraphic card driver issue. Did you look up what resolution is actually available to you right now, and what graphic card you have and such?

When ubuntu first booted up after the install the max avalible resolution was 800x600.
So I opened up something called xserver-xorg (tutorial I found on through google) and added my 1280x1024 res.
Perhaps that's the issue? :(

I can use that res in windows.
The computer is a ThinkPad T60 laptop with the Intel Mobile 965 express graphic chipset.

Both the upper an lower systembar is where they should be. Just that the desktop "continues" up behind the system menu (mouse too).

I thank you all for your efforts to help.
Perhaps I should stick to the virus infested MS...

---

### Post by Daisuke_Aramaki on 2009-04-16
> **ac13 said:**
> When ubuntu first booted up after the install the max avalible resolution was 800x600.
So I opened up something called xserver-xorg (tutorial I found on through google) and added my 1280x1024 res.
Perhaps that's the issue? :(

I can use that res in windows.
The computer is a ThinkPad T60 laptop with the Intel Mobile 965 express graphic chipset.

Both the upper an lower systembar is where they should be. Just that the desktop "continues" up behind the system menu (mouse too).

I thank you all for your efforts to help.
Perhaps I should stick to the virus infested MS...

can you post your xorg.conf please? its just a resolution thing, and can be easily rectified. Let me see if i can help. Post your xorg.conf. It must be in /etc/X11/

---

### Post by crazypeppo on 2009-04-16
It is a display issue and simple. I can't remember what I did to fix it, I had the same thing before. System>Preferences>Appearance>Visual Effects ...maybe set it to normal or none and see if it happens. I too recall I played with my resolution as well... Good luck

---

### Post by ac13 on 2009-04-16
Again, thank you. The ubuntu people are too nice :)
Unfortunately I gave in to the frustration (experianced a couple of other issues too, prob easily fixed though).
So I switched back to MS.

I will meditate on this and get back on the horse at some later point. Need to get some work done on the computer right now.

Peace.

---

### Post by prem1er on 2009-04-16
Wow. I think that wast the fastest re-conversion? I have ever seen. Anyone else?

---

