---
title: "Notifications pop-up seems misplaced in desktop"
date: 2009-11-18
forum: Desktop Environments
---

### Post by surfinmdq on 2009-11-18
Hi, I think the notification pop-up is misplaced in my desktop because it shows way down the main top panel.

I would like to know if any other user have this same issue, if by chance there isn't any issue at all and this is the correct behaviour and, finally, if anybody knows any way to set the coordinates X,Y where the notification pop-up should appear.

I add a screenshot as example, please forgive the mess of the desktop :P

[http://dl.dropbox.com/u/3033493/notificacion.jpg](http://dl.dropbox.com/u/3033493/notificacion.jpg)

Any suggestion welcomed, thanks!

---

### Post by wojox on 2009-11-18
It was put there so people can hit the close/min/max buttons without dismissing the dialog.

---

### Post by emigrant on 2009-11-18
me too had the same thing when i ran karmic through live cd. not sure whether its a reso problem or thats the default. lets wait for others to speak ;)

---

### Post by surfinmdq on 2009-11-18
Hi guys,

@wojox: not it isn't because when you mouse over the pop-up it will fade AND let you see what's behind it and even interact with anything there's there, call it a windows frame, a file in you desktop of so.

@emigrant: I'm starting to think if it could see a Emerald issue. Please confirm you're using Emerald.

Best.

---

### Post by wojox on 2009-11-18
> **surfinmdq said:**
> Hi guys,

@wojox: not it isn't because when you mouse over the pop-up it will fade AND let you see what's behind it and even interact with anything there's there, call it a windows frame, a file in you desktop of so.

@emigrant: I'm starting to think if it could see a Emerald issue. Please confirm you're using Emerald.

Best.

What about those of us who don't use compiz and it doesn't fade?

---

### Post by emigrant on 2009-11-18
> **surfinmdq said:**
> Hi guys,



@emigrant: I'm starting to think if it could see a Emerald issue. Please confirm you're using Emerald.

Best.

no. in live cd i cant use emerald :D

---

### Post by surfinmdq on 2009-11-18
So, Emerald is out of question.

I wonder now why of it's behaviour, in all the KK screenshots I see the notification pop-up is well up next to the panel.

Would be *great* to have a way to edit where the notification will appear.

---

### Post by bluelamp999 on 2009-11-18
Take a look here - [http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html](http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html)

---

### Post by PhilGil on 2009-11-18
As bluelamp pointed out, there is a work-around to revert to the old position, but the Karmic notifications are definitely there by design: [http://www.mail-archive.com/ayatana@lists.launchpad.net/msg00742.html](http://www.mail-archive.com/ayatana@lists.launchpad.net/msg00742.html)

I personally dislike the new location, but I'm not fussy enough to bother with the work-around.

---

### Post by surfinmdq on 2009-11-18
Guys, you defenitely ROCKS!  :popcorn:

Thank you very much. Post closed.

---

### Post by dlzerocool on 2009-12-08
thank you so much, what a strange choice to move the popup there...

Since you move the mouse over it, it become transparent and you can click trough it there's no real excuse to change the position...
I first tough that was because the close button of the windows...
but no you can click even if the osd is shown...

Anyway the .deb worked nicely.
<< Ubuntu 9.10 karmic x64

---

### Post by nallen00 on 2010-01-02
Firstly, I've reviewed all of the documentation on this issue.  After considering the myriad excuses (including the importance of aesthetics) presented by the development team, it's my opinion that the current positioning looks (and is) ridiculous - much like parking your car 10 feet from the curb to accommodate visitors who rarely, if ever, visit. That would look *silly*, wouldn't it...?

Questions and considerations:

[LIST]
[*]How many people find themselves needing to manipulate window controls when a notification is present...?
[/LIST]
[INDENT][I]This seems to be the overriding argument for offsetting async notifications.  It bugs the heck out of me, for the simple fact that the most frequent notifications are async, and because they're async, are offset directly over important tools (when maximized).  Exactly what we're trying to avoid, right #-o  Yes...it's possible to click THROUGH the popup, but the fundamental idea is to ACKNOWLEDGE the notification, either by closing it or clicking on it to open the notifying program...
[/I]
[LIST=1]
[*][B]SOLUTION - Combined Notifications (Drawer)
[/B]
[/LIST]
[INDENT]*A single "drawer" (similar in appearance to the current "balloon") that slide-fades from the top-right beneath the panel, or from directly under it.  If appearance is as important as the developers claim (and it is) then merging notifications is the only option.  Disjoint notifications of any kind (stacking, ballooning, etc.) will only look flaky and half-baked (sort of how they do now)...*

*The "drawer" should also allow MEANINGFUL user interaction, however limited it may be. For instance, it should be possible for the user to acknowledge the notification by closing it directly, rather than relying on some obscure (and incredibly annoying) click-through scheme.  I don't know about you, but when I mouse-over a notification, I intend to interact with the notification, not close a window or perform a search...*

*Another example is the case of "queued" notifications, where several popups are activated simultaneously.  In these cases, user acknowledgement would force the popup to slide-fade IN, and immediately slide-fade OUT to display the next notification.*  This characteristic would also apply autonomously (the popup times-out), and help to catch the user's eye during notification changes.
[/INDENT][/INDENT]Just my 2 cents, but something has to be done about this.  It looks horrible, and suffers from a complete lack of functionality.  It doesn't need to be overcomplicated or bloated with customizations, just streamlined.  The "drawer" outlined above would definitely accomplish this, giving the desktop a more integrated feel, and inject some *much*-needed practicality.

---

