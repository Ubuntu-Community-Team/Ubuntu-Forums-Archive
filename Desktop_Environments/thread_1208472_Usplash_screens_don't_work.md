---
title: "Usplash screens don't work"
date: 2009-07-09
forum: Desktop Environments
---

### Post by ontwowheels on 2009-07-09
Hello,

I haven't had much luck installed different usplash screen on two of my 9.04 systems.  I have loaded the start up manager, installed several usplash screens from gnome-look.org on two different systems.  All but one of my new usplash screens don't work.  The stock usplash works and just one other does but the rest don't.  Am I missing something?  Is it a version issue?

THANKS

---

### Post by VCoolio on 2009-07-09
I haven't had luck installing usplash themes with startupmanager. Installing manually does work though (at least with themes from gnomelook that explicitly mention to be compatible with jaunty).

Assuming you're trying to use the theme "myusplash.so" run these lines:

remove old link:
```
sudo rm /usr/lib/usplash/usplash-artwork.so
```

copy new splash:
```
sudo cp /path/to/myusplash.so /usr/lib/usplash/
```

create link to new splash:
```
sudo ln -s /usr/lib/usplash/myusplash.so /usr/lib/usplash/usplash-artwork.so
```

reconfigure:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

To use the old jaunty usplash again:
```
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so && sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by ontwowheels on 2009-07-09
Thanks, I'll give that a try.

---

