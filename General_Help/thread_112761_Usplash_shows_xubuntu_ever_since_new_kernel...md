---
title: "Usplash shows xubuntu ever since new kernel.."
date: 2006-01-05
forum: General Help
---

### Post by eXcentra on 2006-01-05
Well, the Usplash has never worked for me in the beginning but ever since I got the new kernel, it shows the usplash. The only problem is that it shows the xubuntu logo. This doesn't bother me much but eventually, i would want to find out how to change it. Let that time be now. :)
So... how do i change the usplash to the default ubuntu one? I think this has something to do with me having XFCE installed and then updating the kernel. :|
I've tried reinstalling ubuntu-artwork and usplash and completely removed xfce and the xfce usplash.
Any ideas?

---

### Post by AmboyGuy on 2006-01-05
I have the same thing happening. Did you try removing the xubuntu-artwork-usplash package ? 

I noticed that when I booted into the original kernel (12-9.23) the ubuntu splash runs, and when I boot into the latest updated kernel (12-10.25) the xubuntu splash is used.

I have to look into the usplash a little more but I haven't been rebooting a lot since I dropped windows a couple of months ago.

---

### Post by kingsidy on 2006-01-05
remove the xubuntu-desktop package, and reinstall the kernel image. that is how i got the ubuntu slapsh screen back. make sure u install the kernel image for the one you are not using first. like if you use 386, install the kernel for 686 while you are using 386.

---

### Post by carlosqueso on 2006-01-05
Ah, I thought it was just me....I love the little mouse, and since I"m an xubuntu user, it fits 8-).  Thanks for the explanation of why.

---

### Post by whoisvince on 2006-01-05
I was able to fix that problem by doing this after removing the xubuntu-artwork-usplash package:
```
sudo apt-get install --reinstall usplash
```
then
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by eXcentra on 2006-01-07
[QUOTE=whoisvince]I was able to fix that problem by doing this after removing the xubuntu-artwork-usplash package:
```
sudo apt-get install --reinstall usplash
```
then
```
sudo dpkg-reconfigure linux-image-`uname -r`
```[/QUOTE]
Hooray, it worked! Thanks a bunch. :D

---

