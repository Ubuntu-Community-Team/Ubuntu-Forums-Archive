---
title: "What is the best way to sync files between computers?"
date: 2009-06-19
forum: General Help
---

### Post by chrisbooth12 on 2009-06-19
I just recently bought a new Dell Mini 10 with XP. I went ahead and put Ubuntu on it (Jaunty, not UNR). I also have my main laptop with Jaunty on it as well. I download a lot of music and putting all that music on my Dell Mini is a tedious process for me. I usually just do it from a USB drive. I do have drop box installed but really only use that for small files and not albums of music. What would be the best way to sync files between the two? Would it best best just to use SMB and share both homefolders on both computers? Is their a package out there that can do this for me automaticlly so I dont have to copy new music over by hand?

---

### Post by KeyserSoze93 on 2009-06-19
you may want to read the man page, but in principle you should run something like this from your laptop:

```
rsync -av desktop:/home/you/Music /home/you
```

You will need to install openssh-server on your desktop
```
sudo apt-get install openssh-server
```

I use rsync all the time to sync my desktop and laptop and it works like a dream.

---

### Post by raymondh on 2009-06-19
> **KeyserSoze93 said:**
> you may want to read the man page

I use rsync all the time to sync my desktop and laptop and it works like a dream.


+1 on both man page and rsync

---

### Post by chrisbooth12 on 2009-06-20
Thanks for your help ill check it out. I did a quick scan of the main page thanks

---

### Post by dcstar on 2009-06-20
> **chrisbooth12 said:**
> I just recently bought a new Dell Mini 10 with XP. I went ahead and put Ubuntu on it (Jaunty, not UNR). I also have my main laptop with Jaunty on it as well. I download a lot of music and putting all that music on my Dell Mini is a tedious process for me. I usually just do it from a USB drive. I do have drop box installed but really only use that for small files and not albums of music. What would be the best way to sync files between the two? Would it best best just to use SMB and share both homefolders on both computers? Is their a package out there that can do this for me automaticlly so I dont have to copy new music over by hand?

unison

---

