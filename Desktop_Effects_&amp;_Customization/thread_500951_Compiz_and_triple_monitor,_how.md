---
title: "Compiz and triple monitor, how?"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by B3rt on 2007-07-14
I am using Ubuntu 7.04 with triple monitor setup using 2x nvidia 6200 cards (1x agp and 1x pci)

The triple monitor is working fine but i cannot get compiz to work, when i try to enable it I only get a message that it cannot start, no error message.

Can someone tell me how to get this to work?

---

### Post by un_dave on 2008-06-25
I think the issue with this is that Xrandr, which is required for compiz, conflicts with xinerama, which is what enables you to have the 3 monitors setup as the same desktop.

I have the exact same issue, and was asking about it here: [http://ubuntuforums.org/showthread.php?t=840063](http://ubuntuforums.org/showthread.php?t=840063)

It all seems to come back to the xrandr/xinerama conflict. If you do get this to work, i'd love to know how.

---

### Post by ad_267 on 2008-06-25
Can you set up three monitors with TwinView? I know it's called "Twin" but I'm just wondering because I know you can't use compiz with two monitors unless you use TwinView.

---

### Post by un_dave on 2008-06-25
I'd guess no. TwinView is something created and supported by Nvidia, and was made so that the two outputs of the graphics card can be accessed by the operating system as if it were one display. I'd doubt they've implemented this to work across 2 graphics cards.

---

### Post by ad_267 on 2008-06-25
> **un_dave said:**
> I'd guess no. TwinView is something created and supported by Nvidia, and was made so that the two outputs of the graphics card can be accessed by the operating system as if it were one display. I'd doubt they've implemented this to work across 2 graphics cards.

Ahh ok maybe not then. It was just a guess as I could get compiz working using TwinView but not Xinerama.

---

### Post by un_dave on 2008-06-25
The reason this works is because with TwinView enabled, xinerama is not required.
Interestingly though, the wikipedia article on Xinerama ([http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama)) states this:

*As of 2008, Xinerama is planned to be deprecated in the future by X.org in favor of XRandR [1]. X.Org had convened a standards committee to document the protocol and API as formal standards, but that effort has now ended. [2]. Development of the Xinerama code is now hosted on freedesktop.org and managed by X.Org.*

Which I thought implies that we should be able to use Xrandr to achieve the same thing as Xinerama. Then with out the dependancy on xinerama, we would be able to use compiz. 

However, no one as yet has been able to explain to me whether this functionality is possible, or planned with Xrandr.

---

