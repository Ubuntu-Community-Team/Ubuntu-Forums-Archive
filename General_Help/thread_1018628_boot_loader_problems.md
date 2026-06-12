---
title: "boot loader problems"
date: 2008-12-22
forum: General Help
---

### Post by Patterns on 2008-12-22
Alright so far I've been here and recieved information about moving my wubi installation to another partition. That failed. It froze while copying files. Vista partition was wiped clean. When booted message said operating system not found. So I reinstalled Vista on my old partition. Ubuntu is still on its own partition but there isn't a boot loader for it anymore. I've been searching for hours trying to fix this but no dice. I also downloaded wubi and created a new partition and installed ubuntu on it hoping I could get all my files off of my other installation, but still no boot loader for it.

Please help..

---

### Post by caljohnsmith on 2008-12-22
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Patterns on 2008-12-22
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

I don't have a live cd..

---

### Post by caljohnsmith on 2008-12-22
In Windows, try looking for the Ubuntu ISO image in C:\ubuntu\install\ubuntu-8.10-desktop-i386.iso. Or search the C:\ubuntu directory for any ~700 MB file, and that will most likely be the Ubuntu ISO. If you can burn that to a CD (make sure to burn it as an ISO image and not as a data CD), you can use that.

---

### Post by Patterns on 2008-12-22
> **caljohnsmith said:**
> In Windows, try looking for the Ubuntu ISO image in C:\ubuntu\install\ubuntu-8.10-desktop-i386.iso. Or search the C:\ubuntu directory for any ~700 MB file, and that will most likely be the Ubuntu ISO. If you can burn that to a CD (make sure to burn it as an ISO image and not as a data CD), you can use that.

Ugh alright, so I had to download the disc. I installed it on two different cds and both times when I select a menu option it freezes. The disc drive stops moving as well. >.<

---

