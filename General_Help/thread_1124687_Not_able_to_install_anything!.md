---
title: "Not able to install anything!"
date: 2009-04-13
forum: General Help
---

### Post by Goggeli on 2009-04-13
Hello!

I'm not able to install anything any more! I get this msg in terminal:"reading database...dpkb: serious warning: the file list for the package "privoxy" is missing.."

I must have deleted some files in my system by mistake... Anyone now what I can do? while this privoxy thing is missing I can't update or install anything, and that is a problem! I hope I don't have to re-install ubuntu, because I don't have too much time at my hands atm.

Thanks for all help!!!

- Goggeli

---

### Post by zvacet on 2009-04-13
Try in synaptic mark privoxy package for reinstall.Do you really need proxy?If you do read [this.]("https://help.ubuntu.com/community/Privoxy")I hope it will be helpful to you.

---

### Post by Goggeli on 2009-04-13
Thanks! And no, I don't need it! tried to re-install it and to do a complete removal of it! All tough, it fails! I get the same msg first about it's missing, and then I get the same fails as I posted about in this post: [http://ubuntuforums.org/showthread.php?t=1113923]("http://ubuntuforums.org/showthread.php?t=1113923")
I don't understand a thing at this point! everything works well, except installing and removing programs and applications!

---

### Post by zvacet on 2009-04-13
```
sudo apt-get --purge remove privoxy
```

---

### Post by Goggeli on 2009-04-13
Still same errors, just now in the terminal! and I get a crashreport, as allways!

---

### Post by zvacet on 2009-04-14
```
sudo dpkg --remove --force-remove-reinstreq privoxy
```

---

