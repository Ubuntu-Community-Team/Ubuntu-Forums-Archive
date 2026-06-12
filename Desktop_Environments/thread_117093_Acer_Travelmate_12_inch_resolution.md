---
title: "Acer Travelmate 12 inch: resolution"
date: 2006-01-14
forum: Desktop Environments
---

### Post by sroets on 2006-01-14
I have a resolution problem with my Acer 12 inch notebook
1280*800 resolution is not in my list

I followed the instructions from another topic:
(sudo gedit /etc/X11/xorg.conf)

but when I look in that file, the 1280*800 is all over the place
>> how do you get the resolution in the list ???

---

### Post by 23meg on 2006-01-14
Did you look into [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973")?

---

### Post by sroets on 2006-01-14
[QUOTE=23meg]Did you look into [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973")?[/QUOTE]

No, I was looking in another thread

Seems to be very usefull information, thanks!
Heve been trying to look for the 855 resolution package in Synoptic, but I do not find it. So - newbie as I am - I am still stuck I am afraid...

---

### Post by 23meg on 2006-01-14
What's the "855 resolution package"? I'm not sure I get where you're stuck; please elaborate.

---

### Post by sroets on 2006-01-14
see the following answer in [another thread]("http://www.ubuntuforums.org/showthread.php?t=43321&page=3&highlight=855resolution"):


I have tried Breezy, and everything expect sound and ACPI works out of the box. If you want WPA, you'll have to install the wpa_supplicant package (it s in the repositories). And you will also have to install the 855resolution /that's also in the repositories) package to get the screen resolution right.

---

### Post by sroets on 2006-01-14
or this [thread on Travelmate 3000 series]("http://ubuntuforums.org/showthread.php?t=43321&highlight=travelmate+3004"):

Be aware that for using that very nice resolution, 1280x800, you will need the "855resolution" script. Once installed, everything is fine.

---

