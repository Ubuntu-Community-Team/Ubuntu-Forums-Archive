---
title: "video not working"
date: 2009-05-28
forum: General Help
---

### Post by blastbar on 2009-05-28
hiya i can watch videos on you tube fine but not videos from other sites any clues?
   Cheers

---

### Post by fillintheblanks on 2009-05-28
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

good luck

---

### Post by albinootje on 2009-05-28
> **blastbar said:**
> hiya i can watch videos on you tube fine but not videos from other sites any clues?

Can you post the output of the following :
```

dpkg -l|grep flash
dpkg -l|grep swf

```

And are you using Firefox scripts like NoScript ?

---

### Post by blastbar on 2009-05-29
thanks for your replies the link you sent has made it work fine sorry albinootje i dont really understand what u are saying to do :(

---

### Post by blastbar on 2009-05-29
o oh video works fine now on everything apart from you tube  i can get audio on it just not vid ???? anyone know?????

---

### Post by blastbar on 2009-06-01
hiya yeah more problems now when ever i put anything in teminal i get this:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 any help?

---

### Post by Soul-Sing on 2009-06-01
```
sudo rm /var/cache/apt/archives/lock
```

(with running no -apt or synaptic or dpkg on the background.)
to kill dpkg: ```
sudo killall dpkg
```

---

### Post by blastbar on 2009-06-01
thank you for replies its all coming together nicely =]

---

