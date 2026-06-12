---
title: "atlantis plugin"
date: 2009-10-14
forum: Desktop Environments
---

### Post by cesar71 on 2009-10-14
can some one please show me how to get Atlantis 2, the fish inside the 3d cube, I'm using 9.10 beta:( please help

---

### Post by ankspo71 on 2009-10-15
Hi,
It might be in the package* compiz-fusion-plugins-unsupported*   (but I can't guarantee it's in there) found here:
[https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")
The instructions on how to install are on the page.
Be sure to select: **Display sources.list entries for: Karmic (9.10)**.
James.

---

### Post by cesar71 on 2009-10-15
ok im sorry but from my understanding, forgive me i am new, the website 

[https://launchpad.net/~compiz/+archive/ppa/+packages?field.name_filter=compiz-fusion-plugins-unsupported&field.status_filter=published&field.series_filter=]("https://launchpad.net/%7Ecompiz/+archive/ppa/+packages?field.name_filter=compiz-fusion-plugins-unsupported&field.status_filter=published&field.series_filter=")

contains the plugins. :confused: how do i install them?

---

### Post by Capt. Blackwood on 2009-10-15
Here you go, step by step instructions:
 
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)
 
 
Your best bet is to open that link in a seperate window. That way, it's there and you can continue installing. 
 
 
Good luck.
 
 
BTW, thanks for finding that Atlantis Plugin. I've been lookin for it for days.
 
 
Rock on,
:guitar:
 
 
Btw, it's cool to be a n00b. I'm not that much of a n00b now, but i ain't a pro. You'll get it. Have faith.

---

### Post by ankspo71 on 2009-10-15
No problem,

First you need to add 2 lines of code to your sources list.

So open up your terminal and type the following:
```
sudo gedit /etc/apt/sources.list
```Your text editor will open up with a bunch of urls...
Next, copy these following lines and paste them into the bottom of the sources list.

```

deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main 
```Next, save the file and close it.

The installation by Synaptic:
Go to Synaptic Package Manager and open it.
Next click on the Reload button at the top,
Next search for:
*compiz-fusion-plugins-unsupported*
Then check the box to install it,
Then click on Apply.

Optional installation by terminal:
```

sudo apt-get update
sudo apt-get install compiz-fusion-plugins-unsupported
```Do you already have CompizConfig Settings Manager installed? If you don't you will need that too, as well as a 3D capable graphics card driver.
James

---

### Post by ankspo71 on 2009-10-15
> Btw, it's cool to be a n00b. I'm not that much of a n00b now, but i ain't a pro.
Same here :P

---

### Post by Capt. Blackwood on 2009-10-15
If i remember the driver also needs to be activated. 
 
I think it's System -> Administration -> Hardware Drivers. 
 
make sure the driver is actived, indicated by a green dot next to the driver name.

---

### Post by ScarySquirrel on 2010-02-22
Thanks. This page has really helped me, especially the post where I get to add the repositories. 

I just added them in Synaptic, searched for compiz, and found compiz-fusion-plugins-unsupported in the list!

I'll try installing it, and let you know if it breaks my installation.

Er, if it breaks my installation, maybe you won't hear from me.

How about you'll hear from me if it DOESN'T.

---

### Post by LatinHacker on 2010-02-23
It works WONDERFUL on 9.10:P

---

