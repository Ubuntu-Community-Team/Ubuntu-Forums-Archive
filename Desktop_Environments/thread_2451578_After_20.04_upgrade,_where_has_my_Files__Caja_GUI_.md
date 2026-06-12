---
title: "After 20.04 upgrade, where has my Files / Caja GUI gone?"
date: 2020-10-07
forum: Desktop Environments
---

### Post by dhduncan on 2020-10-07
I updated my Ubuntu to 20.04 LTS  a few days ago, and to celebrate I have started using the default desktop environment instead of MATE.

I mostly love the change, but, as stupid as this must sound to experienced folk, I can't find a file management GUI!  I was using **Caja** with MATE and I believe that I might expect to find something called **Files** with the desktop I am currently using, but I can't find either in the application list or via the main desktop search function.

What am I doing wrong?

I should say that when I download a zipped archive and choose to view files after expanding, Caja does launch... but why doesn't it appear among the applications?

---

### Post by deadflowr on 2020-10-07
File managers like caja and nautilus  have entries in their respective .desktop files
which read as OnlyshowIn that makes them only show up in whichever desktop environment they are for.
caja is set to only show in mate.
(The .desktop files are found in /usr/share/applications, fwiw)

(there is also a reverse of this with a NotShowIn option too, so an application is forced not to show in certain instances)

It's designed this way for exactly the scenario you're doing.
Having multiple desktop environments installed, this prevents having duplicate programs show, more or less.


Anyway, it seems odd not to have Files, is nautilus installed?
```
apt policy nautilus
```

How did you install regular Ubuntu?

---

### Post by dhduncan on 2020-10-07
Thanks for the explanation, that makes a lot of sense, including giving me some idea why Caja could be invoked by the archive manager even if I couldn't see it.

This issue is resolved. The technical issue I mean, not the root issue of my foolishness.

I have since executed 
```
sudo apt install ubuntu-desktop
``` and Files is now present.  

My original installation of ubuntu (18.04) was, I was reminded by my friend, a MATE distro.  So I upgraded to 20.04 by accepting a prompt from the package manager, and then was using regular ubuntu from the login prompt.  So i guess that was less than a proper installation and I was still perhaps trapped in some kind of MATE universe.

Nautilus is present too, though i only ran the query after I had done the command line install so whether it was there before I can't say.

Should I be removing MATE somehow? I am not going back.

---

### Post by ActionParsnip on 2020-10-07
Try:
```

sudo apt-get --reinstall install caja

```

Will probably help

---

