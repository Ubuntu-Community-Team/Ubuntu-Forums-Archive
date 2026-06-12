---
title: "boot splash"
date: 2005-12-16
forum: General Help
---

### Post by Chris Tucker on 2005-12-16
i have ubuntu isntalled, and i have added kubuntu-desktop amoung other window managers, and many kde apps, i use kde occasionally.

i have since got the 686 kernel, and now use it over the 386.
my problem is at boot time, just after grub, only when using 686, loading modules and such, the screen shows the Kubuntu logo, how do i change it to the regular ubuntu one?

---

### Post by hod139 on 2005-12-16
I'm not positive, but using [this thread]("http://www.ubuntuforums.org/showthread.php?t=82835") as a guide, I think you have to
remove kubuntu-artwork-usplash
```
 sudo apt-get remove kubuntu-artwork-usplash 
```
reinstall usplash
```
 sudo apt-get reinstall usplash 
```
Regenerate the initramfs:
```
 sudo dpkg-reconfigure linux-image-$(uname -r) 
```

---

### Post by the_one on 2006-07-16
"Sudo update-alternatives --config usplash-artwork.so"  You'll see both splash screens listed. Just enter the number to select the ubuntu splash and that should bring back the original splash when you reboot.

---

