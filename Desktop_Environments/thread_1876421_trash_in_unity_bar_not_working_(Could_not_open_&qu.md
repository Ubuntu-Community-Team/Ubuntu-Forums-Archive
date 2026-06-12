---
title: "trash in unity bar not working (Could not open &quot;trash:&quot;  Archive type not supported)."
date: 2011-11-06
forum: Desktop Environments
---

### Post by gra1 on 2011-11-06
Hi,

I have just upgraded from 11.04 to 11.10 and have problems opening some icons from unity side panel,with the error message(example), Could not open "trash:"
Archive type not supported.

This error also occurs on inserted  usb, dvd, drives etc.
These folders can all be accessed from the home folder with no problems.
Any one any ideas on how to sort out.

Thanks

---

### Post by mc4man on 2011-11-06
There will be a nautilus upgrade shortly that will take care of this, only affects upgrade installs.

You can fix now in several ways - one way would to do what the update to nautilus is going to do, in a terminal run this
```
sudo ln -s /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus-folder-handler.desktop
```

Otherwise you could as shown here
[http://ubuntuforums.org/showthread.php?p=11393051#post11393051](http://ubuntuforums.org/showthread.php?p=11393051#post11393051)

---

### Post by gra1 on 2011-11-06
Thanks for that,

icons now work in unity bar as they should.

---

### Post by ckaloli on 2011-11-10
Thank you, had a problem with VLC opening my mounted devices.

---

