---
title: "How can I get Gnome's Ambience theme from 10.10 in 10.04?"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Extol11 on 2010-10-28
Hi! I'm still using the 10.04 Ubuntu distribution in this computer and don't plan to change it until it's support is over. I just noticed the new 10.10 version has a crisper, better-looking version of the ambiance theme and I'd like to know if there's anyway of replacing the version of ambiance in 10.04 for the one in 10.10. I searched about this before and didn't find any thread explaining how to get it done. Thanks in advanced.

---

### Post by maverick555 on 2010-10-28
gnome-look.org look for ambiance redefined.thats the only closest one i found.

---

### Post by Jahid65 on 2010-10-28
```
sudo add-apt-repository ppa:webupd8team/light-themes
sudo apt-get update
sudo apt-get upgrade
```

Then you have maverick's default theme

---

### Post by Extol11 on 2010-10-28
> **Jahid65 said:**
> ```
sudo add-apt-repository ppa:webupd8team/light-themes
sudo apt-get update
sudo apt-get upgrade
```

Then you have maverick's default theme

This will only update the theme and nothing else, right? I want to absolutely stay on 10.04.

---

### Post by Extol11 on 2010-10-29
> **Jahid65 said:**
> ```
sudo add-apt-repository ppa:webupd8team/light-themes
sudo apt-get update
sudo apt-get upgrade
```

Then you have maverick's default theme

Tried it and it worked. Thanks a whole freakin' lot!

---

