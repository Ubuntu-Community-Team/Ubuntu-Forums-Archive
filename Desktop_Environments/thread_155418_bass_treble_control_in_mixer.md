---
title: "bass treble control in mixer?"
date: 2006-04-05
forum: Desktop Environments
---

### Post by mrweirdo on 2006-04-05
is there a way to get bass and treble controls in the mixer panel in ubuntus gnome? I come from on windows with a creative sound blaster 5.1 card that has drivers for it and software that includes mixer were you can control those such things along with a bunch of other features of the card. Not realy woried about the extra features like EAX environments etc but mayby thats doable as well.

---

### Post by Perfect Storm on 2006-04-05
Right click on the 'Volume Control' (The speaker you see in the upper right corner in the panel) and click Open Volume Control.
In the 'Edit' tab choose Preferences. Now add the extra you want.

---

### Post by mrweirdo on 2006-04-09
hrm that added the controls but unfortunately they don't seem to do anything for my sound card. The bass and treble  stays the exact same no matter how i adjust them.

---

### Post by Baji on 2006-09-08
what fixed the issue for me was enabling the Tone switch in the alsamixer (audigy 2 ZS)

---

### Post by MrCreosote on 2006-12-13
Oh my god.. thank you so much.. 

recap:

this works with my live! 5.1 gamer edition (but i guess any Live! version will work):

If your bass and treble aren't working just right-click the speaker (upper-right thingy you know?) choose "open volume control" click EDIT -> PREFERENCES and check "TONE"

cheers

---

### Post by boast on 2007-03-23
> **Artificial Intelligence said:**
> Right click on the 'Volume Control' (The speaker you see in the upper right corner in the panel) and click Open Volume Control.
In the 'Edit' tab choose Preferences. Now add the extra you want.

treble and bass aren't options.

---

### Post by Perfect Storm on 2007-03-23
Try if you can find it in;
```
alsamixer
```

---

### Post by boast on 2007-03-23
it wasn't there either.

Does onboard sound not get such options?

---

### Post by Perfect Storm on 2007-03-23
I'm not sure, I don't think so, it can be the onboard card that isn't fully supported yet. But that is just a guess. I have been searching the forum, but havn't found anything useful.

---

