---
title: "Monitor gives &quot;Frequency out of range&quot; error"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Tommy2k4 on 2006-06-26
I've been using kubuntu dapper for a few weeks now and have had this error around 10 times, 4 of them were today :mad: It doesn't happen on boot up like most of the other posts I found with this same error. It happens for no apparent reason, although a couple of the times happened when I was taking screenshots, but other times I wasn't.

What happens is any music playing will stop, the monitor will show lots of multicolored vertical lines, then after a few seconds it will change to an error saying "Attention - 31K / 0Hz Frequency out of range". the num lock light also goes off (if that makes any difference) and pressing ctrl alt f6 doesn't bring up the console so I don't know what the problem is. I rebuilt xorg.conf using dpkg-reconfigure and (after adding 1280x1024) this is my config. 

[http://paste.ubuntu-nl.org/16559](http://paste.ubuntu-nl.org/16559)

Someone in IRC recommended changing VertRefresh to 30-160 but that made no difference either. 

I don't have a screensaver on either.

Thanks, Tommy

---

### Post by Tommy2k4 on 2006-06-26
Sorry if double posting/bumping isn't allowed but this problem is still happening :( Someone suggested that I add "acpi=off noapic nolapic" to the end of the kernel in grub menu.lst but that didn't solve it either :( 

Does anyone have any idea what could help fix it?

---

### Post by Sonofmoog on 2006-06-26
I took a look at your xorg.conf and it looks okay.  I'd consider backing down the resolution and color depth until you can get a better handle on your problem, so you might try changing default mode to 16, which should drop you to 1024 x 768 and 16 bpp.  That's not a fix, just a suggestion for a workaround.  HTH

---

### Post by Dubbayoo on 2006-06-26
Make sure those are the right HorizSync and VertRefresh numbers for you monitor. You might also want to try a modeline generator. 

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)

---

### Post by Tommy2k4 on 2006-06-26
Is there a console command to find out what refresh rates my monitor can support? I'm sure I've done it before but I can't remember it. This is a 15" CRT and that page for the modline says it shouldn't be done on 15" or less so I won't bother with that. I really don't want to use 1024x768 but I suppose I could try it for a while and see if the crashes stop.

---

