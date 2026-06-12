---
title: "How can I play my DVD collection on Ubuntu?"
date: 2009-02-21
forum: General Help
---

### Post by WolfyAU82 on 2009-02-21
This is something I've been trying to sort out on and off since I ditched Windows.  I have a stack of DVD movies (local region btw) and I can play them on the family video player and my PS3, just not my PC running Unbuntu...

I've downloaded all the "Gstream" packs that give you MPEGs, AVIs, Flash and so on...  But still there are no codecs readily available to download from the Apps Manager that will allow the use on DVD videos purchased from your local record shop, video library and so forth.

I'm not just asking this one for own sake but I'm trying to give a friend a convincing argument in favour of making "The Switch".

Is there any solution out there that will allow me to play DVD Videos without having to resort to ripping my entire collection? (as MPEGs, AVIs and so on are the means of watching a movie on my PC)

---

### Post by dorkdork777 on 2009-02-21
Yes!

First of all, [add the repos as shown here.]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Then, just run this command:
```
sudo apt-get install libdvdcss2
```

...and with any luck, you should be able to play DVDs just fine. :)

EDIT: Just to let you know, you can do all this stuff with GUIs, instead of the command line. It's just much easier for us to tell you to issue these commands than give you intricate instructions on how exactly to navigate in the GUI to the option you need. ;)

---

### Post by handy on 2009-02-21
If you need more than the above, then you should find everything you need in the following link:

*_[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)_*

---

### Post by WolfyAU82 on 2009-02-23
Thanks guys! It's working a treat :D

I'll let my friend know

---

