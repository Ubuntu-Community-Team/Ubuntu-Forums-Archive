---
title: "cannot mount ntfs disk - help with terminal"
date: 2009-04-12
forum: General Help
---

### Post by tunznath on 2009-04-12
Hi all
I have a dual boot xp and hardy computer, and there is a problem with the XP side and it hung, and cannot be rebooted - When trying to acces it from ubuntu i get this dialog box, I tried the option of forcing it, but it says this option is only available to root, how do i get to be root and if it means using su or sudo what is the correct syntax for this?

also the dialog says at your own responsibility - why? what can go wrong if anything?
thanks in advance

---

### Post by benj1 on 2009-04-12
```
gksu nautilus
```
will start nautilus in root 

although im not sure why its giving you all these errors so if your not sure i would hang fire for some one who knows about such things

---

### Post by taurus on 2009-04-12
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by tunznath on 2009-04-12
the windows side didnt shut down properly and had to be reset/forced to quit, and now ubuntu cant mount the second hard drive because it is still in "use" by the forced quit windows -

---

### Post by tunznath on 2009-04-12
thanks taurus - what do all the other things do?
apt get update etc?

dont want to lose anything on it

---

### Post by taurus on 2009-04-12
Basically, you need to install ntfsprogs package to use ntfsfix to fix that error with your ntfs filesystem since you can't boot windows to do a proper shut down anymore.

---

### Post by tunznath on 2009-04-12
Hi taurus
Thanks  - so it wont delete anything on the ntfs disk?

---

### Post by taurus on 2009-04-12
No.  But if you don't feel comfortable running those commands, then you shouldn't.

---

### Post by tunznath on 2009-04-12
Hi Taurus - 
Thanks a million - ran the code and it worked and can now get access to my other disk   - Its not that i didnt feel comfortable running the code - I just like to know what it is doing so that I can learn the shell
Many thanks once again 
Nath

---

### Post by tunznath on 2009-04-12
Hi Taurus - 
Thanks a million - ran the code and it worked and can now get access to my other disk   - Its not that i didnt feel comfortable running the code - I just like to know what it is doing so that I can learn the shell
Many thanks once again 
Nath

---

### Post by -kg- on 2009-04-12
ntfsprogs - [Read all about it.]("http://www.linux-ntfs.org/doku.php")

An interesting page with lots of information.

---

### Post by colau on 2009-06-27
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
Will ntfs-3g do the job too for this case?

---

