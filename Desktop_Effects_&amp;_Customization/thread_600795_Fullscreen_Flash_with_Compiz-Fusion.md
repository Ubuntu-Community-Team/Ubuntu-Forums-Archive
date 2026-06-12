---
title: "Fullscreen Flash with Compiz-Fusion"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by accessd on 2007-11-02
I'm running the latest Flash 9 beta on Ubuntu 7.10 amd64 with Firefox 2.0.07 (32 bit). The fullscreen functionality in flash videos works great when Compiz is not running. However, when Compiz is running, the video opens in a new window instead of going fullscreen. When I turn off the "Legacy Fullscreen Support" option in the Workarounds plugin, the video will go fullscreen for a second, but will then revert back to it's original state within the browser window. Does anyone know how to fix this?

The first screenshot shows Flash in fullscreen mode without Compiz running, and the second one shows it with Compiz running (notice the little window tucked in the right-hand corner of the screen, that is the video).

TIA

---

### Post by scontin on 2007-12-07
If not present install "Advanced Desktop Effect settings" , then  uncheck "Unredirect fullscreen windows" in "General Options" and "Support legacy fullscreen" in the plugin "Workaround".
For me has been a definitive solution.:popcorn:

---

### Post by AsoSako on 2007-12-16
This does work.  Thank you!  :)

---

### Post by doorknob60 on 2007-12-18
Yay! THis works with me too :D Thanks!

I just hope the disabling the Legacy full screen thing doesn't mees up anything else...

---

### Post by redseventyseven on 2008-01-18
> **scontin said:**
> If not present install "Advanced Desktop Effect settings" , then  uncheck "Unredirect fullscreen windows" in "General Options" and "Support legacy fullscreen" in the plugin "Workaround".
For me has been a definitive solution.:popcorn:

It nearly worked. Unfortunately, since I have a dual monitor setup, it didn't quite come off. The "small window" problem was solved, however the fullscreen video came out like in the attached image. The left screen had a small portion of the video displayed but the right screen didn't have any. (The black rectangle represents the "invisible" part of my desktop, because my screens are different resolutions.)

I'll have a little play around and see if I can sort it - however if anyone knows a quickfix for this problem (to save me looking) I'd be very grateful!

---

### Post by redseventyseven on 2008-01-18
OK, I have a bodge-job solution, but not completely satisfactory. By leaving "Support legacy fullscreen" checked (but still unchecking "Undirect fullscreen windows") I still get the small 200x200 pixel window, but at least this time I can maximise it to fill one of my screens without it disappearing.

UPDATE: In fact that still works regardless of what state "Unredirect fullscreen windows" is in. What does that option actually do?

---

### Post by SEBASTIANFFX on 2008-02-12
Thank you!!
It works Great!!:):popcorn:

---

### Post by GMeola on 2008-02-18
Nice quick fix... Worked perfect.

---

### Post by willstoney on 2008-02-26
Worked for me too!

---

### Post by nidelius on 2008-03-03
It works I get it up in full screen. But it's laggy. Anyone else experiencing this?

---

### Post by sofamensch on 2008-03-04
Yes. Also laggyness here. I know my friend has it too. Seems to be quite common and goes away when compiz is turned off.

---

### Post by bouss on 2008-03-05
Worked perfectly... thanks a lot.

P.S. Had some hard time with translation of these since I use greek Ubuntu. So for the greeks who have the same problem first one is same but "Support legacy fullscreen" is translated as "&#928;&#945;&#961;&#945;&#948;&#959;&#963;&#953;&#945;&#954;&#942; &#933;&#960;&#959;&#963;&#964;&#942;&#961;&#953;&#958;&#951; &#928;&#955;&#942;&#961;&#959;&#965;&#962; &#927;&#952;&#972;&#957;&#951;&#962;" while "workarounds" will be found as "&#924;&#959;&#957;&#964;&#943;&#966;&#949;&#962;"

Thx again.

---

### Post by melat0nin on 2008-04-06
I too have the problem with it lagging in fullscreen.  Any thoughts on a fix for this?

---

### Post by nomanstown on 2008-07-10
hey guys,

[B]Fixed: System Sources did not update instantly. Now, after updating them, everything is fine.
[/B]
I have added all sources on this world to my system sources and I (as a good old Windows idiot) also rebooted.
But still Synaptic is not able to find anything about compizconfig-settings-manager, just like the terminal.
I tried to install it manually but it required some things I don't really understand, can't find and can't install.

What can I do to install compizconfig-settings-manager?

Ubuntu Gutsy Gibbon, Firefox, any updates installed.

PS: I can not upgrade to the newest Ubuntu version, because of sound.

HELP PLZ!!!

---

### Post by NovruzeliH on 2008-07-11
lol it works fine for me wihtoit doing this :P

---

