---
title: "hold libnotify popups"
date: 2009-06-09
forum: Desktop Environments
---

### Post by bayonetblaha on 2009-06-09
Is there no way to make libnotify display messages longer, or display them until I click on them? Does anyone know if libnotify will get features like these in the near future?

---

### Post by hellocatfood on 2009-06-09
I too am wondering this. Is there an options menu for libnotify?

---

### Post by bayonetblaha on 2009-06-09
I sent an email to Christian Hammond, the lead developer, asking about future developments like persistant notifications and reply boxes.  

The only options I can find are in gconf-editor under apps/notification-daemon.  It lets you decide what corner the boxes appear in, the theme to use, and what sounds to play, if any.  A great start, to be sure. I just hope that trend continues, so that libnotify can be more flexible and reach its potential.

---

### Post by abhiroopb on 2009-06-09
Unfortunately the new libnotify popups in jaunty (IMHO) are quite useless. While they are pretty and look "slick" and "shiny", in terms of usability they serve no purpose.

When a friend comes online on pidgin I can't interact with the popup to either start a chat or do anything else, making the popups relatively useless and forcing me to use guifications. 

Anyway in answer to your question I remember reading that Ubuntu does not intend to add any interactive features in the near future.

---

### Post by sabre2th on 2009-06-09
> **abhiroopb said:**
> Unfortunately the new libnotify popups in jaunty (IMHO) are quite useless. While they are pretty and look "slick" and "shiny", in terms of usability they serve no purpose.

When a friend comes online on pidgin I can't interact with the popup to either start a chat or do anything else, making the popups relatively useless and forcing me to use guifications. 

Anyway in answer to your question I remember reading that Ubuntu does not intend to add any interactive features in the near future.
If I remember correctly, that was kind of the point when the new notifications came about.  Bayo seems to be more concerned with how long they're staying on the screen, which I would agree is not always long enough.

I am not aware of any option to control how long they stay on the screen, but I would like to see one.

---

### Post by abhiroopb on 2009-06-09
Thats true, I guess I should have clarified and said he cannot "click" on them to make them disappear.

And yes that was most certainly the point of them, and it is a cool idea in principle, but on a practical day to day use, I'd rather use the older version which allowed me to click on the popups.

---

### Post by sloggerkhan on 2009-06-09
I like the new version solely because it doesn't interupt nexuiz with a huge fps drop like the old system did.

---

### Post by bayonetblaha on 2009-06-09
I agree with you abhiroopb, there's a lot of functionality that could be added to libnotify.  I think it's great that someone came up with a unified notification system that a lot of programs use, though. I love getting gnome-do twitter, rhythmbox, transmission, firefox, network manager, and pidgin notifications all in the same place.  Now that advantage can be multiplied if more features are added to libnotify, since those features will improve all programs using it! If only.

---

### Post by bayonetblaha on 2009-06-09
and let's not forget, as sloggerkhan noted, that libnotify seems (to me) to be incredibly solid, basic though it may be.

---

### Post by abhiroopb on 2009-06-09
In addition there is a firefox addon called firefox notify that tells you when your download is complete!

---

### Post by bayonetblaha on 2009-06-09
Christian's response, for those who are interested:

"libnotify can set a timeout of 0 to indicate that the notification should stay on-screen until acknowledged. However, it's best to only use this when it's absolutely crucial that the user respond to it, and really in that case, a dialog is more appropriate most of the time.

@reply or pidgin replies are possible, but isn't something that libnotify itself has to do. There should be plugins for pidgin to use notifications, and there's some apps out there that show twitter @replys (but I don't know the names off-hand)."

So it would seem that the application controls how long the message is displayed.  That makes sense, I guess.

---

