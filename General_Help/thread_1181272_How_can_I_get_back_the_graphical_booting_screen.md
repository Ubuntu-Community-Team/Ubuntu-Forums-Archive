---
title: "How can I get back the graphical booting screen?"
date: 2009-06-07
forum: General Help
---

### Post by colau on 2009-06-07
Hi,
The ubuntu 9.04 system is booting with text today.I don't know why it came.
How can I get back the graphical boot screen?

---

### Post by cybergalvez on 2009-06-07
> **colau said:**
> Hi,
The ubuntu 9.04 system is booting with text today.I don't know why it came.
How can I get back the graphical boot screen?

What does the screen say? are you at a login prompt or some other prompt?

---

### Post by colau on 2009-06-07
> **cybergalvez said:**
> What does the screen say? are you at a login prompt or some other prompt?
I get the login screen.Everything is all right.
But before I get the login screen,it is a text based loading,there is no splash screen with progress-bar.

---

### Post by BlazeFire247 on 2009-06-07
Is it some sort of terminal? Mine does the same too, black background; white text.

---

### Post by merlinus on 2009-06-07
You may need to add

splash

to the end of the line in /boot/grub/menu.lst that boots ubuntu.

---

### Post by QIII on 2009-06-07
Could you post the contents of your menu.lst?

---

### Post by colau on 2009-06-08
> **QIII said:**
> Could you post the contents of your menu.lst?
```

splashimage=(hd0,2)/boot/grub/splashimages/nature.xpm.gz

title		Ubuntu 9.04
uuid		36e71d07-0150-44f6-9b95-72e54ad5aa2b
kernel		/boot/vmlinuz-2.6.29-020629-generic root=UUID=36e71d07-0150-44f6-9b95-72e54ad5aa2b ro quiet splash 
initrd		/boot/initrd.img-2.6.29-020629-generic
quiet

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by x33a on 2009-06-08
try reverting to the original splash image, and see if it makes a difference.

```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by Legace on 2009-06-08
If the above doesn't work, try:
```
gksudo gedit /etc/usplash.conf
```

Make sure the X and Y values are correct.

Then type in:
```
sudo update-initramfs -u
```

---

### Post by colau on 2009-06-08
> **x33a said:**
> try reverting to the original splash image, and see if it makes a difference.

```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

```

sudo update-alternatives --config usplash-artwork.so

There is no program which provides usplash-artwork.so.
Nothing to configure.

```

---

### Post by colau on 2009-06-08
> **Legace said:**
> If the above doesn't work, try:
```
gksudo gedit /etc/usplash.conf
```

Make sure the X and Y values are correct.

Then type in:
```
sudo update-initramfs -u
```
usplash.conf
```

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=800
yres=600

```
Are these value correct?

---

### Post by x33a on 2009-06-08
hi colau, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=304331](http://ubuntuforums.org/showthread.php?t=304331)

---

### Post by maheshasolkar on 2009-06-08
You might want to check if the steps mentioned in the following bug fix your problem (not sure if it applies, but worth a try):

[https://bugs.launchpad.net/ubuntu/+bug/205990](https://bugs.launchpad.net/ubuntu/+bug/205990)

---

### Post by colau on 2009-06-09
> **x33a said:**
> hi colau, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=304331](http://ubuntuforums.org/showthread.php?t=304331)
I did this
```

sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so sudo dpkg-reconfigure linux-image-$(uname -r)
ln: target `linux-image-2.6.29-020629-generic' is not a directory

```
Same result.
Does anyone have any idea?

---

### Post by colau on 2009-06-09
```

cd /usr/lib/usplash/
ls -l
lrwxrwxrwx 1 root root 36 2009-05-11 13:49 [COLOR="Red"]usplash-artwork.so[/COLOR] -> [COLOR="Red"]/etc/alternatives/usplash-artwork.so[/COLOR]

```
The font with red color has a black backgroud color.

---

### Post by colau on 2009-06-09
Solved.
Downloaded it from [here]("http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386")
and installed the deb package.
After that 
```

sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so
sudo update-initramfs -u

```

---

