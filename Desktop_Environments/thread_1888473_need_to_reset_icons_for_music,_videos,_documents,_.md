---
title: "need to reset icons for music, videos, documents, etc"
date: 2011-11-29
forum: Desktop Environments
---

### Post by srihari29691 on 2011-11-29
Hi,
I'm running 10.10, GNOME...
I happened to try a local language for the interface recently that renamed all the folders in home -music, pictures, docs, videos, etc... these names did not revert after switching back to English so i deleted and created new folders with English names.

However, I now have the **default folder icon** for all the folders in my home directory... How do i change the icons for these?! changing the icon theme isn't changing anything...

---

### Post by BC59 on 2011-11-29
> **srihari29691 said:**
> Hi,
I'm running 10.10, GNOME...
I happened to try a local language for the interface recently that renamed all the folders in home -music, pictures, docs, videos, etc... these names did not revert after switching back to English so i deleted and created new folders with English names.

However, I now have the **default folder icon** for all the folders in my home directory... How do i change the icons for these?! changing the icon theme isn't changing anything...

You can install Ubuntu Tweak 

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

There is an option to manipulate the default folders.

---

### Post by srihari29691 on 2011-11-29
Hey, thanks for the tip...
I restored the default folders...
It fixed the icons for Desktop, Music and Documents...
But the icons for Videos and Pictures still remain unchanged...
what do you think is the problem?

---

### Post by BC59 on 2011-11-30
I had the same problem once but after restoring they changed automatically. There is something left which impedes them from restoring.

You can do it manually. Right click on Videos, properties and from the first tab Basic click on the icon of Videos. Opens a browser to find and choose another icon. Depends which icon set you use. You can select new icons from pixmaps which folder is shawn on the left pane. I think the default Radiance-Ambiance for 11.10 are stored on /usr/share/icons/.

---

### Post by srihari29691 on 2011-11-30
I was just going to try changing the icon manually,
and voila! It was already changed...

A mysterious reboot had fixed the problem! :)

---

### Post by BC59 on 2011-11-30
Yes I told you, this is the normal, the system recognizes the folders and is doing that automatically.

---

