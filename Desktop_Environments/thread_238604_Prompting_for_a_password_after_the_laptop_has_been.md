---
title: "Prompting for a password after the laptop has been close"
date: 2006-08-17
forum: Desktop Environments
---

### Post by prizrak on 2006-08-17
Ok I tried looking trough the documentation and searching the forum. However I still can't find anything on this.

When I close my laptop's lid it locks the screen. I can't find any way to stop it from doing that. It gets annoying to put my password in everything I move from one room to another.

I already unchecked "Lock screen when screensaver is active". The Power manager is set to default "Blank screen when closing the lid" setting. 

I guess that's about all the info I can think off. 

Thanks

---

### Post by justynbutler on 2006-08-18
Hi, sorry no solution but I have the exact same problem. Hopefully someone on the forums can point out the obvious box to uncheck so we can go kick ourselves. ](*,) 

Justyn

---

### Post by justynbutler on 2006-08-18
It's done. Just go to System -> Preferences -> Power Management, then under **Actions** change "When laptop lid is closed" from "blank screen" to "do nothing".

Make sure you do this for both "Running on AC" and "Running on battery".

I had previously not tried it because I had assumed that it would prevent the laptop screen from being turned off when the lid was closed, which is undesirable, however this isn't the case.

I feel this setting is very unclear!

Hope this helps people.

Justyn.

---

### Post by prizrak on 2006-08-18
> **justynbutler said:**
> It's done. Just go to System -> Preferences -> Power Management, then under **Actions** change "When laptop lid is closed" from "blank screen" to "do nothing".

Make sure you do this for both "Running on AC" and "Running on battery".

I had previously not tried it because I had assumed that it would prevent the laptop screen from being turned off when the lid was closed, which is undesirable, however this isn't the case.

I feel this setting is very unclear!

Hope this helps people.

Justyn.

You, my friend, are the man. Thank you very much, I would have never thought of that. That setting is EXTREMELY unclear, I thought the same thing as you did. 

Now if we could only find the setting that is responsible for the password prompt it would be awesome. I remember it being very obvious in Breezy but we got gnome-screensaver instead of x-screensaver so unchecking "lock screen" is not turning off the password prompt anymore. Hibernate will still ask for a password though. Maybe just something that Gnome needs to implement.

---

