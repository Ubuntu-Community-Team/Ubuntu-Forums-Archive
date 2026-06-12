---
title: "Admin password login no longer dims screen"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Bluemystr on 2005-10-13
I orginally updated my existing Ubuntu installation to the then Colony 3 release through the Internet and was pleased with the effect of the screen dimming when the administration password was required leaving the login dialog the only bright part of the screen.

About a week ago through my normal updates this behavior vanished from my system.

Unfortunatly, when the dialog now appears (without the screen dimming effect) as it has no border, if it appears on top of certain windows it is hard to make out.

The screen dimming effect still works on Logout.

Has the screen dimming function been removed from the Admin password prompt or is this just my system?

Many thanks.

---

### Post by dbott67 on 2005-10-13
Have you recently changed your theme?  If so, try changing it back to the default to see if it fixes it.

It happened to me when I changed my theme, but it didn't bother me, so I've never investigated to see if it was related to the theme.

-Dave

---

### Post by Bluemystr on 2005-10-13
[QUOTE=dbott67]Have you recently changed your theme?  If so, try changing it back to the default to see if it fixes it.

It happened to me when I changed my theme, but it didn't bother me, so I've never investigated to see if it was related to the theme.

-Dave[/QUOTE]

Nope, that didn't do it. I had just last week been playing with the themes again to see if I couldn't improve on my custom theme.

I switched back to Human and then checked.

I take it that as the dimming works for you it IS just me and the dimming is still part of Ubuntu.

Thanks.

---

### Post by mcduck on 2005-10-13
well, I wouldn't even know about the dimming if people wouldn't write about it to the forum. Never seen it happen myself :/

---

### Post by bereillyte on 2005-10-13
I noticed this too about a week ago it started. Actually, I prefer it not to dim - guess the developer did too :-)

BTW did n't change anything with themes, backgrounds (anything really)

---

### Post by g14 on 2005-10-14
If you read the ubuntu-devel mailing lists, you would know why this feature was disabled. On many video cards, the effect of it fading for the gtksu and gksudo dialog would appear very choppy.

No fading is better than choppy and broken looking fading. As a result, this was removed.

---

