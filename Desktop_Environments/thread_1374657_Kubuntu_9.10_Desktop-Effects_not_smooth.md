---
title: "Kubuntu 9.10: Desktop-Effects not smooth"
date: 2010-01-07
forum: Desktop Environments
---

### Post by Markus72 on 2010-01-07
Hi,

I have a Thinkpad with Intel GMA 4500HD grafics card and just wonder why effects are not as smooth as I would expect.

No no - I don't only talk about that eye candy things that may require some powerful GPU (although I think that even the GMA should be able to handle this nowadays) I mean even dragging windows when KDE desktop effects are disabled.

Moving windows is not smooth, meaning there could be more screen updates to make movements look fluently.
I'm talking about normal movements which for example look very smooth on a Mac.

Glxgears gives me about 2.000-2.500 fps, so I assume that the grafics driver works well.
CPU usage is also low when moving windows.

I tried to take a look into the xorg.conf to maybe tweak it but there is none since 9.10 and the system configures X automatically.

So, the question is: if we assume the GMA chip is fast enough to do more and the CPU usage is low (and it's not a weak one) - why is the movement not perfectly fluent?

(this is no vsynch tearing issue - it's about the number of redrawings per second)

Any idea? Anyone with similar issues?

Br
Markus

---

### Post by m0o on 2010-01-07
I would suggest upgrading to KDE 4.3.4, a lot of people have claimed more improvements in the UI, snappier responses and smooth drawing. You can grab the packages from the [Kubuntu backport]("https://help.ubuntu.com/community/Repositories/Kubuntu").

---

### Post by Zorael on 2010-01-07
Are the GMA chipsets the same as the Poulsbo ones? With the dreadful drivers?

As for KDE (SC), with 4.4 stuff is considerably smoother (due to new nifties in Qt 4.6), but it's slated for release in February so unless you want to run the beta it's still beyond the horizon.

---

### Post by Markus72 on 2010-01-07
@mOo: I already use 4.3.4...

@Zorael: Do you know if this will be part of 10.4?

---

### Post by Markus72 on 2010-01-07
PS: just saw Ubuntu (Gnome) on a MacBook Pro - looked the same

---

### Post by Zorael on 2010-01-07
> **Markus72 said:**
> @Zorael: Do you know if this will be part of 10.4?
4.4 will be in 10.04, yes. Seeing as 10.04 will be released in April and 4.4 in February, I can't imagine anything else.

4.4 RC 1 should be released any day now; it was [scheduled for release Jan 6th](http://techbase.kde.org/Schedules/KDE4/4.4_Release_Schedule#January_6th.2C_2010:_Release_KDE_SC_4.4_RC_1), but it's apparently been delayed. If you're running Karmic, you can try out the packages available from the kubuntu ppa (at your own peril).

---

### Post by Markus72 on 2010-01-07
Thanks - maybe I'll try it out

---

