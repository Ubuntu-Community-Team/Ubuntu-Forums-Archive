---
title: "unable to install certain application"
date: 2009-01-03
forum: General Help
---

### Post by jrkraj on 2009-01-03
hi friends ,

I am unable to install certain application when every I try to install these application I am getting below error

```

(application) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.



```
my computer configuration 
dule core 1.83
1 G.b ram
giga bite motherbite

---

### Post by LateNiteTV on 2009-01-03
what are you trying to install?

---

### Post by Ryadt on 2009-01-03
Post the output of ```
uname -m
```

---

### Post by LateNiteTV on 2009-01-03
im going to guess that its a windows app.

---

### Post by jrkraj on 2009-01-03
vlc player

---

### Post by LateNiteTV on 2009-01-03
ok, i guess i was wrong.
try following these instructions. [http://www.debianadmin.com/install-vlc-media-player-in-ubuntu.html](http://www.debianadmin.com/install-vlc-media-player-in-ubuntu.html)

---

### Post by Ryadt on 2009-01-03
Your error message is saying that the application you are trying to install is not 32 bit.

Why do you not install vlc from the repos
```
sudo apt-get install vlc
```

---

