---
title: "Xserver not loading"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Doobiedo on 2005-11-14
Hi all.

Just installed ubuntu and am having difficulty getting X to load, any help would be much appriciated

pertinent information:-
error message
  "Data incomplete in file /etc/X11/xorg.conf
      At least one device section is required
  (EE) Problem parsing the config file
  (EE) Error parsing the config file

  Fatal server error: 
  no screens found"


"fatal IO error 104 (connection reset by peer) on X server ":0.0""

i tried editing /etc/X11/xorg.conf to add my monitor but its empty

system specs: 
amd athlon xp 2400+
nvidia geforce 5200
sharp lcd monitor.

if you need anymore info just ask

---

### Post by adwait on 2005-11-14
/etc/X11/xorg.conf is empty?? That is pretty much the reason for X not loading up. Try running
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by invalid on 2005-11-14
```
sudo dpkg-reconfigure xserver-xorg
```
This should clear things up.

If you still have problems after doing this, paste the config file here on the forum so we can inspect it.
```
cat /etc/X11/xorg.conf
```

Cheers,
Cb

---

### Post by Doobiedo on 2005-11-14
Thank you , it worked perfectly

---

