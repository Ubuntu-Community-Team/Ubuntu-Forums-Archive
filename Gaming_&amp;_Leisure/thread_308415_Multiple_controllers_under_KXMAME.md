---
title: "Multiple controllers under KXMAME?"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by Contrast on 2006-11-28
My apologies if this has been covered elsewhere, but I searched the forums and couldn't come up with anything that answered my question.

I'm using KXMAME, and haven't had any problems with it so far, except that I can't figure out how to get a second (or third, fourth, etc.) controller working under it. I currently have /dev/input/js0 for the entry in all joystick device-related fields. I've tried adding /dev/input/js1 to that entry (separate by a space) in all fields, as well as just removing the 0 (since most fields are labeled as "Joystick device *prefix*," and haven't made any progress. I'm using PS2 controllers hooked in through a USB adapter. Any ideas? Thanks in advance.

---

### Post by Contrast on 2006-11-30
Up.

---

### Post by treblesix on 2007-05-12
Hi,

I have just tried using 2 controllers, and it worked ok by putting.........

/dev/input/js

into the device field. set as a normal joystick, and with USB PS pads checked.

Hope this helps!

---

### Post by treblesix on 2007-07-01
did you try this ?

I have just reinstalled Ubuntu on a new hard drive, and did this again, and worked perfect.

---

### Post by Contrast on 2007-07-01
I actually figured this out quite some time ago, just forgot to update my post here. The solution I've actually been using as of late though has just been to create links to /dev/input/js0 and /dev/input/js1 in /dev, as that's where most games seem to look for them by default. Saves the hassle of having to change the settings for every game I play.

Anyway, thanks for the reply. :-)

---

### Post by wingnux on 2007-11-23
Thanks treblesix!! =)

---

