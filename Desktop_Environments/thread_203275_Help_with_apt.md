---
title: "Help with apt"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Brando569 on 2006-06-25
ok i screwed something up and i dont know how to fix it. i added the repo for initng and after i installed the debs for it adept said that there was an update available for it but i wouldnt install it cuz it needs libc6-2.3.6-6

so i downloaded libc6-2.3.6-13 and that said it needed tzdata, so i downloaded that but it keeps giving me this message:

dpkg: error processing tzdata_2006g-2_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2006g-2_all.deb

i have no idea on how to fix it, thinking that it might be mostly installed i go to install the new libc6, and that wont install cuz tzdata isnt correctly installed. i cant remove libc6 either cuz so many things depend on it. im stuck...

---

### Post by .t. on 2006-06-25
initng for Dapper is broken. You'll have to compile it from source if you want it to work. Also why are you downloading different packages? That's a surefire way to break a system if you don't know what you're doing.

---

### Post by ayoli on 2006-06-25
> dpkg: error processing tzdata_2006g-2_all.deb (--install):
trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
tzdata_2006g-2_all.deb
you can also try (at your own risks):
```
dpkg --force-overwrite -i package_name
```
that will overwrite `/usr/share/zoneinfo/Africa/Algiers'
if you want to restore resinstall the package where 
`/usr/share/zoneinfo/Africa/Algiers' was with:
```
apt-get remove locales
apt-get install locales
```
regards.

---

### Post by Brando569 on 2006-06-25
i found libc6 in packages.ubuntu.com and installed the deb from there, that fixed it..

---

