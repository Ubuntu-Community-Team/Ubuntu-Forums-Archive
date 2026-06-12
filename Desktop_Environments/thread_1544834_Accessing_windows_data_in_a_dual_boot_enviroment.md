---
title: "Accessing windows data in a dual boot enviroment"
date: 2010-08-03
forum: Desktop Environments
---

### Post by rahul_cse25 on 2010-08-03
I have a laptop dual booted with windows vista and ubuntu.I downloaded certain movies and music files while using windows vista,which are there in my hard disk,My question is can i access these music and video files when i boot into ubuntu,and can i play them?

---

### Post by JustinR on 2010-08-03
> **rahul_cse25 said:**
> I have a laptop dual booted with windows vista and ubuntu.I downloaded certain movies and music files while using windows vista,which are there in my hard disk,My question is can i access these music and video files when i boot into ubuntu,and can i play them?

Yep, go to **System > Administration > Disk Utility**>

Find your hard drive - and click on the Vista partition and click Mount.

Go to your desktop, and it should now be on your desktop! Find your moves and play them.

To play DVD's and other media though, you have to install 'ubuntu-restricted-extras'. **Applications > Accessories > Terminal**
```
sudo apt-get install ubuntu-restricted-extras
```
Enter in your passwords and enjoy your movie!

---

If you want your hard drive to be automatically there for you on the Desktop, go to **System > Administration > Synaptic Package Manager**

Searched for 'ntfs-config' and install it. It will show up in System > Administration > 'NTFS Configuration Tool'. Find your partition from the list and click 'Enable write support' and your hard drive will automatically be their everytime you bootup for easy acccess to your files.

---

### Post by rahul_cse25 on 2010-08-03
But the space allocated to the Ubuntu partition is very small compared to windows vista,will that create a problem?

---

### Post by JustinR on 2010-08-03
> **rahul_cse25 said:**
> But the space allocated to the Ubuntu partition is very small compared to windows vista,will that create a problem?

Hi, if you have at least 5GB's for Ubuntu then you should be fine. :)

---

### Post by celldweller1591 on 2010-08-03
5GB will be used easily after a few updates and new program installations. Recommended is 10GB atleast for a better ubuntu experience. Mine is 55GB :)

---

### Post by cybrsaylr on 2010-08-03
I've never has any problems getting data from the Windows partition and playing it/using it, while using Ubuntu.

---

