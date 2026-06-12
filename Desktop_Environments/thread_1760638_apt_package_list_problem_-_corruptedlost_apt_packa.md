---
title: "apt package list problem - corrupted/lost apt package list file"
date: 2011-05-17
forum: Desktop Environments
---

### Post by damber on 2011-05-17
It seems the last time I was in a wifi 'hotspot' zone, ubuntu decided to update package lists, and overwrote one of the package list files with the html response from the wifi proxy....

Which means this file:  
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages 

..is now corrupted and unusable.

I have tried to clean and update:

apt-get check
apt-get clean
apt-get update

no joy.  

Where can I download this file manually?  Or is there a way to fix this automatically?

Cheers

---

### Post by wildmanne39 on 2011-05-17
> **damber said:**
> It seems the last time I was in a wifi 'hotspot' zone, ubuntu decided to update package lists, and overwrote one of the package list files with the html response from the wifi proxy....

Which means this file:  
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages 

..is now corrupted and unusable.

I have tried to clean and update:

apt-get check
apt-get clean
apt-get update

no joy.  

Where can I download this file manually?  Or is there a way to fix this automatically?

Cheers

Hi, first open terminal type 
sudo dpkg --configure -a then 
sudo apt-get update and that should fix the problem.:D

---

### Post by damber on 2011-05-17
Thanks for the response.

Tried this, though unfortunately still no joy... Exact error message when running sudo apt-get update is:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Essentially this happened when the file was corrupted (contained the proxy web page html), when the file was missing (I deleted it) and with an empty file.  

I've tried installing a VM with a fresh install of Ubuntu to get a copy of that file.. though it was empty, so I guess this way will require me to install a similar set of apps/etc to get a working file... which isn't very practical.

Any other suggestions?  surely I should be able to rebuild this list somehow?

---

### Post by damber on 2011-05-17
OK.. looks like I've fixed it.

Sigh... in my haste I missed that the error after I removed the erroneous file was for a *different* file... the names looked so similar at first glance that I thought they were the same.

So, the simple fix was to delete the erroneous files in /var/lib/apt/lists/ (it was actually most of the files in that directory), and run apt-get update.   :-)

---

### Post by wildmanne39 on 2011-05-18
> **damber said:**
> OK.. looks like I've fixed it.

Sigh... in my haste I missed that the error after I removed the erroneous file was for a *different* file... the names looked so similar at first glance that I thought they were the same.

So, the simple fix was to delete the erroneous files in /var/lib/apt/lists/ (it was actually most of the files in that directory), and run apt-get update.   :-)
H, so your problem is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:D

---

### Post by damber on 2011-05-18
oops, almost forgot!  

Thanks

---

### Post by alroger on 2011-05-18
Thank you for the tip.
I have no proxy, so don't know how it happened. I just got back from a weeks trip and it was like that.
I just remove everything in the lists dir and then the update started working again. Natty 64bits here.

---

