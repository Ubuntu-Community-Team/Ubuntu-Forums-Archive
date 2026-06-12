---
title: "[SOLVED] plez help cant install"
date: 2008-03-22
forum: Desktop Environments
---

### Post by tropcky on 2008-03-22
i just got the deb file for second life  and when i was installing it  my internet disconnected  so its crashed so i close it  by the crash quieter force  after reboot  when i trayed to install ig agen i got thes msg 
  any help pleeez

---

### Post by tropcky on 2008-03-22
plez guys help   

when i tryed to do sudo apt-get install -f   i got 

 The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

---

### Post by overdrank on 2008-03-22
> **tropcky said:**
> plez guys help   

when i tryed to do sudo apt-get install -f   i got 

 The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

Hi and you can try ```
sudo apt-get remove --purge "package name"
```

---

### Post by tropcky on 2008-03-22
thank u for helping me   but thes didnt work with me 

but it sloved now by :

sudo dpkg --remove --force-remove-reinstreq secondlife-install

thes make it works with me   

and thank agen for helpin

---

