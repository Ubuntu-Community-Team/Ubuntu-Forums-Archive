---
title: "Can't login, disk full?"
date: 2008-12-16
forum: General Help
---

### Post by KameZero on 2008-12-16
So, whenever I attempt to login to KDE it boots me back to the login screen, I checked around and apparently my hard drive is full. So, I go around and delete some stuff and my hard drive is still full apparently. The odd part is that live CDs also report the hard drive is full even after deleting large files.

df -h reports:
Filesystem     Size      Used    Avail    use%    mount
/dev/sda1      146G      138G    0        100%     /

Any ideas?

---

### Post by taurus on 2008-12-16
After deleting large files, did you remember to empty your trash bin since those files still take up the same disk space in your trash bin.  At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
That should buy you some disk space so you can log into KDE again.

---

### Post by Casper Hansen on 2008-12-16
Try 

```
sudo apt-get autoremove
```

or

```
sudo apt-get purge [nameoflargeprogram]
```

---

### Post by KameZero on 2008-12-16
> **taurus said:**
> After deleting large files, did you remember to empty your trash bin since those files still take up the same disk space in your trash bin.  At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
That should buy you some disk space so you can log into KDE again.

Huh. That freed up about 200 meg which let me login and empty the trash, freeing up about 8 gig. Does deleting stuff with rm still send it to the trash?

Thanks for the help guys.

---

### Post by Polygon on 2008-12-16
deleting anything with 'rm' will delete the file permanently, it does not send it to any trash.

---

### Post by drs305 on 2008-12-16
Here's some info on Trash and a few other things you can do to get a bit more disk space if you want to learn more:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

