---
title: "Google Earth 5 startup issue"
date: 2009-02-15
forum: General Help
---

### Post by summersk on 2009-02-15
Newbie!! (Ive also posted in the Apple section)

Ubuntu ver. 8.10 installed on an Macbook 2GHz (dual-boot)

I've installed Google Earth ver 5.0 
When trying to start I get the following error:Could not create directory:

/root/.googleearth/Cache

Then when I click "OK" I get the following:

Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:

My Places Path: "/home/username/.googleearth"
Cache Path: "/home/username/.googleearth/Cache"

The program tries to load then quits at the question of the day
I've turned off the Visual Effects to "None"

What should I try next?

Linux username-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Hardware: Macbook 2.0 GHz 1GB MB

---

### Post by johnjohn2 on 2009-02-15
in terminal type > googleearth 
and then take a screenshot and upload here

Thanks john

---

### Post by sloggerkhan on 2009-02-15
I had a similar issue, turned out it was crashing on trying load some something or other - lib.so file. Found latest version of lib package for debian and force installed it. Google earth then ran, but my package manager decided my packages weren't happy and when I had it resolve its problem automatically, google earth no longer worked again.

---

### Post by hyperdude111 on 2009-02-15
Go to /home/*yourname*/google-earth and re-name the file "libcrypto.so" to "libcrypto.so.bak" then it will work.

You may have to do it as root, is so use "sudo nautilus" the the same

---

### Post by johnjohn2 on 2009-02-15
> **hyperdude111 said:**
> Go to /home/*yourname*/google-earth and re-name the file "libcrypto.so" to "libcrypto.so.bak" then it will work.

You may have to do it as root, is so use "sudo nautilus" the the same
not in your home
You usually only need to be root outside your home directory

---

