---
title: "dual-screen setup (Intel): primary monitor?"
date: 2009-01-28
forum: Desktop Environments
---

### Post by Ace_NoOne on 2009-01-28
While I love Intrepid's dual-screen handling, there is one thing that's really bugging me:
An external monitor connected to my laptop[1] is always treated as the primary screen, which is fairly annoying in many regards (e.g. desktop icons, GNOME panels[2], window locations).

I could find instructions for [NVIDIA]("http://ubuntuforums.org/showthread.php?t=486809&page=3") and [ATI]("http://ubuntuforums.org/showthread.php?t=301941") graphics cards, but there doesn't seem to be anything about my feeble Intel chip (GMA X3100 / 965GM).

How can I make Ubuntu treat my laptop monitor as the primary screen?
Any help would be greatly appreciated!


[1] [HP Compaq 2510p]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-306995-3355633.html")
[2] There's a way to position GNOME panels on another screen though:
```
gconftool-2 -t int -s /apps/panel/toplevels/bottom_panel_screen0/monitor 1
```

---

### Post by Ace_NoOne on 2009-02-03
Sorry to bump this, but perhaps someone will have a suggestion now...

---

### Post by skoorbevad on 2009-02-05
Give this a look:

[http://ubuntuforums.org/showpost.php?p=6683308&postcount=9](http://ubuntuforums.org/showpost.php?p=6683308&postcount=9)

...also, what do you mean by "primary" screen?  You can drag the gnome-panel to whichever screen you want it to appear on, and the location will remain so long as you're saving your session properties.

Window placement tends to follow mouse locations in most situations, check CCSM or gnome appearance prefs for more info.

---

### Post by Ace_NoOne on 2009-02-06
Thanks for the response, skoorbevad!

> **skoorbevad said:**
> Give this a look:
[http://ubuntuforums.org/showpost.php?p=6683308&postcount=9](http://ubuntuforums.org/showpost.php?p=6683308&postcount=9)
That looks interesting (I have also struggled with the 2048x2048 limitation for Compiz).
However, I'm not entirely sure how it relates to this particular issue. Will read through it again later, make sure I understand it properly.

> **skoorbevad said:**
> what do you mean by "primary" screen?
That's a good point, actually.
I suppose what counts is the monitor arrangement, as everything's simply measured from the upper left corner? (That would also explain placement of desktop icons, for example, since the external monitor's to the left of my laptop.)

**Update:** I just realized it's not quite that simple; notifications (e.g. Thunderbird, libnotify) sometimes appear on the laptop/secondary screen (i.e. absolute lower right), but sometimes in the lower right of the external/primary screen.

> **skoorbevad said:**
> the location will remain so long as you're saving your session properties
I must admit, I don't know whether I'm doing that, or how - I simply shut down via the GNOME Main Menu (occasionally also *shutdown -h*).

---

### Post by Craig73 on 2009-02-10
> **skoorbevad said:**
> Give this a look:

[http://ubuntuforums.org/showpost.php?p=6683308&postcount=9](http://ubuntuforums.org/showpost.php?p=6683308&postcount=9)

...also, what do you mean by "primary" screen?  You can drag the gnome-panel to whichever screen you want it to appear on, and the location will remain so long as you're saving your session properties.

Window placement tends to follow mouse locations in most situations, check CCSM or gnome appearance prefs for more info.

It would seem that on my laptop (intel 855GM), the gnome toolbars also insist on being on the external monitor (which is weird because a key use of the external monitor is for a projector... so why would the toolbars be on the external monitor?).  I can drag them to the laptop screen but it would seem that not all programs recognize this (firefox's toolbar is hidden underneath the panel)

---

### Post by Michal Šrajer on 2010-01-22
I created simple script which detects number of monitors and move top-level panels to the next monitor.
Works for me :-)

Cheers,
Michal

---

### Post by joelgrrr on 2010-02-17
That script works for me too (on Karmic). Thanks!

---

### Post by ochampao on 2010-05-11
Amazing :) works perfectly on 9.10. Thanks.

---

### Post by meng1usa on 2010-09-04
amazing! thanks

---

### Post by evelio on 2010-10-11
Thanks! working perfectly on Maverick :)

---

### Post by sumanta679 on 2010-10-28
Thanks! The script works great on 10.10 too. :)

---

### Post by lmivan on 2011-03-01
Wow!!, amazing script!. It works perfectly in 10.10.

Regards, Iván.

---

