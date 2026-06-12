---
title: "Downloaded package files"
date: 2009-04-13
forum: General Help
---

### Post by raam030 on 2009-04-13
Hi all,


I have installed Ubntu 9.04, it indeed better than Vista, also Compiz feature, I am glad to say Mr. Fernis from this forum helped me to do it.. 

Now I am downloading pluggin/codec packages to play MP3, AVI formatts in Movie player. its a big package, took about 1.30 mins to download, Also some other updates.. 

I want to know if there is a way to save these updates seperatly, so that i dont need to download them if I reinstall ubuntu.. 

I have an intention to free some of my HD space dedicate it to ubuntu, and get it installed on that, so I am wondering if there is a way that I could save these updates now and load after I install ubuntu.. ????

Please help me.. 

Raam.

---

### Post by mltucker on 2009-04-13
Hello Raam,

By default these packages will still be on your computer after you install.

The files can be found in the /var/cache/apt/archives directory.

-Mark

---

### Post by kpkeerthi on 2009-04-13
If you happen to reinstall, just copy over the .debs back to /var/cache/apt/archives (on your new install) and run the upgrade (using update manager or apt-get).

---

### Post by raam030 on 2009-04-13
Hi,

Thanks for your reply.... I found them in archive folder. 

Thanks for the help....

---

