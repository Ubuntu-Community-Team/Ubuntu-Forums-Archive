---
title: "help me"
date: 2008-12-06
forum: General Help
---

### Post by darkzlayer on 2008-12-06
whats all about this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i dont know where to fix this error please help me im a beginner in ubuntu

---

### Post by bp1509 on 2008-12-06
d

---

### Post by ibutho on 2008-12-07
Its actually Applications -> Accessories -> Terminal that you need to go to.

---

### Post by lisati on 2008-12-07
You might need to use *sudo* from applications->accesories->terminal: ```
sudo dpkg --configure -a
```
Don't worry if it asks for your password and nothing shows - just type your password as usual, it's part of *Ubunt's security to prevent someone looking over your shoulder.

---

### Post by eternalnewbee on 2008-12-07
One more actually:
It's ```
sudo dpkg --configure -a
```

---

### Post by eternalnewbee on 2008-12-07
I think you need to ```
sudo apt-get update
```
and ```
sudo apt-get upgrade
``` after that, but please correct me if I'm wrong.

---

### Post by darkzlayer on 2008-12-07
Thanks guys. Its working.:popcorn: Anyone has a manual of ubuntu?

---

### Post by eternalnewbee on 2008-12-07
Tutorials & Tips:[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
There you go.

---

### Post by eternalnewbee on 2008-12-07
Btw, every time your problem is solved, please mark it so, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

### Post by abhilashm86 on 2008-12-07
> **darkzlayer said:**
> Thanks guys. Its working.:popcorn: Anyone has a manual of ubuntu?

u can refer [www.yolinux.com](www.yolinux.com) for basics da........

---

### Post by abhilashm86 on 2008-12-07
> **darkzlayer said:**
> Thanks guys. Its working.:popcorn: Anyone has a manual of ubuntu?

what do u mean by manual?is it linux basics or terminal basics???

---

### Post by bp1509 on 2008-12-07
d

---

### Post by darkzlayer on 2008-12-08
Guys I have another problem about my drive

This message came out 

Cannot mount the volume

Unable to mount the volume 'Backup'

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR(usually /)

I might badly type a command or something in the volume tab

How can I return this drive back to normal?

I'm dual booting M$ windows xp and ubuntu...

---

