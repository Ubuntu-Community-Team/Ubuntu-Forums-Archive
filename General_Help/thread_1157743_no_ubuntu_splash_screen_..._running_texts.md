---
title: "no ubuntu splash screen ... running texts"
date: 2009-05-13
forum: General Help
---

### Post by kimikrishna on 2009-05-13
i have just upgraded to jaunty..

but the ubuntu logo with the progress bar tht loads when computer is started is not showing up.

instead it says something like "image not found" 
and continues to run texts..

"reading files needed to boot [ok]
asdasd asfasd uhfver [ok]
sometext sometext [ok] 
.
.
.
.
.
.
.
.
more lines like this..

how do i get back that ubuntu logo with loading progress bar ??

---

### Post by kimikrishna on 2009-05-13
now, 
i installed gnome-splash-manager from synaptic

what to do now?

---

### Post by KhurramM on 2009-05-13
add splash to the end of the line starting with kernel in

/boot/grub/menu.lst

remove text if it is there.

If this fails:

U might also see that the vga values are correct for your system.

add vga=ask to the same above line in the end.

Hope u get it working.

---

### Post by drs305 on 2009-05-13
Run this command to see if the usplash theme is installed:
```
sudo update-usplash-theme
```

If nothing is listed:
```

sudo apt-get install usplash-theme-ubuntu

```
Reboot.

If you have listings, select one:
```

sudo update-alternatives --config usplash-artwork.so

```
Reboot


If something is shown, it could be your UUID changed and is affecting the ability to display the splash image although I don't recall getting a 'not found' message in cases like this.
```

sudo blkid -c /dev/null | grep 'swap'  && cat /etc/initramfs-tools/conf.d/resume # Compare UUIDs
gksu gedit /etc/initramfs-tools/conf.d/resume  # If different, update this file.
sudo update-initramfs -u # update initramfs
sudo reboot # reboot

```

---

### Post by kimikrishna on 2009-05-13
NO. it did nt work :( 

it is saying erros like 

init: resume image not found



also when shutting down, its not playing the logo with the rollback of the bar

---

### Post by kimikrishna on 2009-05-13
@drs305 i am trying your method now

---

### Post by kimikrishna on 2009-05-13
> sudo apt-get install usplash-theme-ubuntu

thnx.. 

i got it working now !

---

