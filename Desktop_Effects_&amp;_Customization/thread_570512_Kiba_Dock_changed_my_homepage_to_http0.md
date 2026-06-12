---
title: "Kiba Dock changed my homepage to http://0/"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by amneziac on 2007-10-08
i was wondering how i can change my homepage back to how it was but still keep kiba dock. Ive tried going into firefox preferences and changing my homepage but it doesnt work
any ideas?

---

### Post by joshuachad on 2007-10-08
lol is that what it was. I installed kiba the other day and was wondering why my homepage changed. But ya you can change that just go to preferences.

---

### Post by amneziac on 2007-10-08
i already tried to fix it by opening firefox then edit>preferences, and changing my homepage but it says its set as the homepage i want but everytime i start firefox it goes to [http://0/](http://0/) and says unable to connect to server or something

---

### Post by DrumScum on 2007-11-23
> **amneziac said:**
> i already tried to fix it by opening firefox then edit>preferences, and changing my homepage but it says its set as the homepage i want but everytime i start firefox it goes to [http://0/](http://0/) and says unable to connect to server or something

Browse to directory ~/.kiba-dock/launcher
Right click on the FF launcher and select preferences.
Go to the "Launcher" tab and change "firefox 0" to "firefox %u"
Shut down and restart kiba-dock.
Fixed.

---

### Post by santiagoward2000 on 2007-11-23
> **DrumScum said:**
> Browse to directory ~/.kiba-dock/launcher
Right click on the FF launcher and select preferences.
Go to the "Launcher" tab and change "firefox 0" to "firefox %u"
Shut down and restart kiba-dock.
Fixed.

That's right! If you're using the lastest Kiba, you can just left-click on the Firefox icon, click on edit and remove the 0 from the exec.

---

### Post by DrumScum on 2007-11-24
> **santiagoward2000 said:**
> That's right! If you're using the lastest Kiba, you can just left-click on the Firefox icon, click on edit and remove the 0 from the exec.

Right, that would be the simple method. Seems like I'm so used to Linux that I automatically go for the "advanced" solution :lolflag:

---

### Post by rune0077 on 2007-11-24
To make it even simpler, you don't need to add the %u in the end. Just remove the 0. Or at least, that's how I fixed it and it works fine.

---

### Post by santiagoward2000 on 2007-11-24
> **DrumScum said:**
> Right, that would be the simple method. Seems like I'm so used to Linux that I automatically go for the "advanced" solution :lolflag:

:lol: I'm still trying to get rid of some Windows attitudes, but I still need to find the simple way around!

---

