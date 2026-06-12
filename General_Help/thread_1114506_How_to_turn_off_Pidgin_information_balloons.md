---
title: "How to turn off Pidgin information balloons?"
date: 2009-04-02
forum: General Help
---

### Post by dodle on 2009-04-02
Is there a way to turn off the balloon pop-up when pointer is over a contact in the main window?

---

### Post by _Purple_ on 2009-04-02
Take a look at this [link](http://pidgin.im/pipermail/support/2008-March/000899.html).

---

### Post by dodle on 2009-04-03
Thank you, very helpful.

---

### Post by _Purple_ on 2009-04-03
My pleasure.

---

### Post by AggravatedGestalt on 2009-11-01
Perhaps a great suggestion, except, this file prefs.xml does not exist. A $whereis, lists no results, and I checked tthe contents of all pidgin folders, and only .so files exist. A complete HD search shows no such file. Thanks anyway though. I must mention that it is becoming a bit much when programmers assume that users should have no right to deactivate extremely stupid features, such as nag balloons. If I do not want to be over-notified, then why should I be unable to not be? Open source? Seems like proprietary bullying to me. It would take an extra 2 minutes for the developers to add such an option to disable the useless/agressive Balloon. How much longer before they are choosing our Desktop images for us? Nonsense! They can stuff their balloons, and all all their other self righteous mutant creations. 

Karmic Koala

---

### Post by peculiar penguin on 2009-11-01
> Perhaps a great suggestion, except, this file prefs.xml does not exist.Really? I've got one in my .purple directory (e.g. ~/.purple/prefs.xml if you're using the default profile location).

But since you resurrected an old thread, which in turn links to an even older post on a mailing list, the file isn't even relevant any more. As 30 seconds on Google just told me, current versions of Pidgin use the global gtk-tooltip-delay setting. You can override this and turn them off by placing the line

gtk-enable-tooltips = 0

in a text file called gtkrc-2.0 in your .purple directory.

> I must mention that it is becoming a bit much when programmers assume that users should have no right to deactivate extremely stupid features, such as nag balloons. If I do not want to be over-notified, then why should I be unable to not be? Open source? Seems like proprietary bullying to me. It would take an extra 2 minutes for the developers to add such an option to disable the useless/agressive Balloon. How much longer before they are choosing our Desktop images for us? Nonsense! They can stuff their balloons, and all all their other self righteous mutant creations.Wow, are you off your meds or something? Calm down, return your Ubuntu and ask for a refund :rolleyes:

---

