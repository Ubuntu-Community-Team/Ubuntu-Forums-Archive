---
title: "Is my swap drive working?"
date: 2009-05-14
forum: General Help
---

### Post by charmsen on 2009-05-14
I am very new to Ubuntu and have limited computer skills. I am trying to verify that my swap drive is working properly. Therefore I executed the following command:

cat /proc/swaps
swapon -s


Following is the response I get:


Filename_______Type_______Size______Used_____Priority
/dev/sda3_____partition__6142968_______0________ -1


I always get the same result, which shows the “Used” as “0”. Does this mean my Swap drive is not working? If not, how do I enable it? I hope someone can help me with my question. Thank you

---

### Post by SoCalChris on 2009-05-14
Since the swap drive is considerably slower than using RAM, it should not be used unless you're completely out of RAM. That's a good thing that it is not being used currently.

Compare that to my Windows box at work, where I'll have 1-2GB of free RAM, and 1-2GB of swap space being used, that doesn't make any sense.

---

### Post by HereInOz on 2009-05-14
Linux -  uses the swap file only when it has no RAM available.

Windows -  seems to use the swap file for anything it feels like, and let not the general user have any clue as to what that is.

If you have 1GB of RAM or more, the likelihood of the swap file being used is rather slim, unless you are running a virtual machine or two.

Enjoy using a system which manages its memory well!

---

### Post by charmsen on 2009-05-14
Perhaps I should have included in my original post why I was asking the question. I am experiencing a suspend problem where my computer locks up if I try to suspend. Many threads have mentioned that a properly functioning swap drive is essential for proper suspension and hibernation.

---

