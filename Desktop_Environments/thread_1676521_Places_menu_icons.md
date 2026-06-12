---
title: "Places menu icons"
date: 2011-01-27
forum: Desktop Environments
---

### Post by The_Aegidius on 2011-01-27
Is it possible to change these icons?

[IMG]http://img9.imageshack.us/img9/8497/tempqt.png[/IMG]

I'm talking about the Documents, Downloads, Music, Pictures and Videos folders. I just changed the icons folders in Nautilus, but they don't change in that menu.

---

### Post by marin123 on 2011-01-27
did you reboot or log out after you installed new icons? try doing that and maybe then they will appear properly.

another thing is that your icon pack doesnt contain that icons so theyre replaced with generic icons like on your picture.

---

### Post by The_Aegidius on 2011-01-27
Thanks for the answer. :)

I restarted but they don't change. As default, i did see the correct icons. I create new folders with that names and delete the older folders in the left panel of Nautilus, and put the news, after update the icons, obviously.

[[IMG]http://img836.imageshack.us/img836/8914/tempae.th.png[/IMG]](http://img836.imageshack.us/i/tempae.png/)

---

### Post by Krytarik on 2011-01-27
Try fixing the icons in the "Places" menu be setting the locations of the personal folders (again) by using "Ubuntu Tweak".
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.
In it choose "Default Folder Locations" in the section "Personal".

---

### Post by The_Aegidius on 2011-01-28
Thank you very much! It works! :D

---

