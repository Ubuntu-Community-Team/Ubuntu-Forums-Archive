---
title: "Monitor Problems"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Arinux on 2006-02-10
Hello everyone,
i Just installed ubuntu on my dektop.My configuration goes as folows:-
Amd 64 3000+
Nforce 4 chipset based motherboard
Nvidia 6600gt pci express
2harddisks, one ide and one sata.

Now the installation was perfectly fine.Only thing in the end of login promt my display is all grabbled up.So how do i fix it up.I am able to use the consoles using cnrl+ f1.Please suggest ya my monitor is Lg studioworks 452V.
Thanks

---

### Post by Lord Illidan on 2006-02-10
Hmm, give us your /etc/X11/xorg.conf

---

### Post by Arinux on 2006-02-11
Okay how do i copy that file, I am using Xp also as dual boot and thats where i connect to the Internet.And what should i do to copy that file and bring it in windows??Then only i can post.I am only getting the login prompt in ubuntu

---

### Post by Jason_25 on 2006-02-11
To get to a virtual terminal from the graphical login screen push ctrl-alt-f2.  Then login.  Now do a ```
sudo nano /etc/X11/xorg.conf
```

You'll need to change the driver in your xorg.conf from "nv" to "vesa".  You can then install the closed nvidia driver   the normal way if you want.

---

### Post by Arinux on 2006-02-11
Hey jason, 
the VESA thing worked , cool
I downloaded the Nvidia driver from there site , when i install them , it says some bin file is missing or provide some path, so how do i install the drivers and how do i check whether my 3d acceleration is working or not?

---

### Post by oscar on 2006-02-11
Following these instructions worked for me:
[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")
I wanted the latest version so I used method 2 but method 1 is easiest and quickest.

---

### Post by handy on 2006-02-11
I use an nVidia GPU, & have used Automatix, to install the nVidia (closed source) drivers on both 64bit & 32bit Breezy 5.10.

Both times totally painless & fast.

Unless you have the time & will enjoy the trip?  I suggest taking the quick route, especially in the very early days of being a linux (Ubuntu) user.

---

