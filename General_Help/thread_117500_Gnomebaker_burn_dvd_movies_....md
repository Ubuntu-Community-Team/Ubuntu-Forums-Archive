---
title: "Gnomebaker burn dvd movies ... ?"
date: 2006-01-15
forum: General Help
---

### Post by dbee on 2006-01-15
I want to burn some (home) movies that I have on my harddrive onto dvd. I'm looking at gnomebaker but it's burn dvd function appears to be for ISO's only.
Is this true ?

---

### Post by DoorGunner on 2006-01-15
to be quite honest I have little experience with gnome baker. I have used K3b but if the two are similar there will be problems trying to get an entire dvd movie from dvd to dvd. I did however follow these instructions today and got lxdvdrip to work prefectly. It was very easy. It will recompress your files so everything fits back on one dvd. 

[https://wiki.ubuntu.com/lxdvdripOnBreezyHowto?highlight=%28lxdvdrip%29](https://wiki.ubuntu.com/lxdvdripOnBreezyHowto?highlight=%28lxdvdrip%29)

---

### Post by dbee on 2006-01-15
I tried the wiki but I seem to only get this 
```

Package mplayer-586 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-586 has no installation candidate


```

... ? I've already added the settings to my sources.list and done an apt-get update.

---

### Post by DoorGunner on 2006-01-15
then

download the following debs from [WWW] [ftp://www.markus-raab.org/apps/:](ftp://www.markus-raab.org/apps/:) lxdvdrip_1.44-2_i386.deb, streamdvd_0.4-9_i386.deb, streamanalyse_0.4-9_i386.deb and vamps_0.97-4_i386.deb 

its actually an ftp site so you could open up an ftp client that you have or you can do what i did and go to [www.markus-raab.org/apps/](www.markus-raab.org/apps/) and it will give you a list of downloads available..... look for
lxdvdrip_1.44-2_i386.deb
streamdvd_0.4-9_i386.deb
streamanalyse_0.4-9_i386.deb
vamps_0.97-4_i386.deb 

down load them by clicking on them.....they more than likely will go to your desktop.....

$ cd /home/yourname/Desktop

then try the rest...it should work for you

It doesnt have a fancy gui....but works just as well in terminal

---

