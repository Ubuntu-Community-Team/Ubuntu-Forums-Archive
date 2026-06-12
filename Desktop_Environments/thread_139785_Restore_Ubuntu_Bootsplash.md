---
title: "Restore Ubuntu Bootsplash?"
date: 2006-03-04
forum: Desktop Environments
---

### Post by samwh on 2006-03-04
I tried xubuntu, didn't like it, uninstalled it, but its bootsplash is still there. How can I restore the original ubuntu one?

---

### Post by o_fortuna on 2006-03-04
[QUOTE=samwh]I tried xubuntu, didn't like it, uninstalled it, but its bootsplash is still there. How can I restore the original ubuntu one?[/QUOTE]
This should be how to do it: From the terminal (Applications-->Accessories-->Terminal):
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```
(copy the commands and paste them in just as they are)

And you should be able to find the Ubuntu usplash. That should be all.

---

### Post by seshomaru samma on 2006-03-26
[QUOTE=o_fortuna]This should be how to do it: From the terminal (Applications-->Accessories-->Terminal):
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```
[/QUOTE]

Can I change the splash screen to a picture of my choice this way as well?

---

### Post by jrib on 2006-03-26
[QUOTE=seshomaru samma]Can I change the splash screen to a picture of my choice this way as well?[/QUOTE]

see [https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

---

### Post by seshomaru samma on 2006-03-27
I followed the wiki but after this command
```
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
```
I get a string of errors like this:
> usplash-artwork.c:317: warning: large integer implicitly truncated to unsigned type


---

### Post by dim4ik on 2006-05-19
[QUOTE=seshomaru samma]I followed the wiki but after this command
```
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
```
I get a string of errors like this:
```
usplash-artwork.c:317: warning: large integer implicitly truncated to unsigned type
```
[/QUOTE]

Hi all,
I have the same situation and get the same errors :-k . Any ideas???

---

