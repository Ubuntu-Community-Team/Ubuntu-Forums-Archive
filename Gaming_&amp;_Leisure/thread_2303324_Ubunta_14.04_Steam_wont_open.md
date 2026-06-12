---
title: "Ubunta 14.04 Steam wont open"
date: 2015-11-17
forum: Gaming &amp; Leisure
---

### Post by samsmith2 on 2015-11-17
Here are the errors i am getting.
~$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-11-17 21:16:08] Startup - updater built Nov 25 2013 18:07:05
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

---

### Post by Bucky Ball on 2015-11-17
*Thread moved to **Gaming & Leisure**.*

---

### Post by samsmith2 on 2015-11-18
bump

---

### Post by ydoc on 2015-11-19
Are you running 32 bit or 64 bit Ubuntu?  

I've got 64 bit on a laptop and I had a heck of a time getting Steam to work.  Not that specific error, but it could be a related issue.  

Check out this link to see if any of this helps:  [http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update](http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update)

---

### Post by ethan27 on 2015-11-28
My laptop an had an issue with steam (Probably not this one) but the easiest solution I've heard and used is:

```
sudo apt-get purge steam
```

This is to remove the current steam installation.

```
sudo apt-get install -y steam
```

This is to reinstall steam with all the dependencies directly from the Ubuntu repository.

Hope this helps. :)

---

