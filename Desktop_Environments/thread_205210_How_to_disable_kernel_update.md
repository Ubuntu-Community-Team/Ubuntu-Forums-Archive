---
title: "How to disable kernel update?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by mickutz on 2006-06-28
Could anyone tell me how could I disable the kernel update, because I don't want to reinstall nvidia drivers every few days...? 

Thanks

---

### Post by linuchsan on 2006-06-28
linux-image is kept back by default as far I know.

---

### Post by tseliot on 2006-06-28
[QUOTE=mickutz]Could anyone tell me how could I disable the kernel update, because I don't want to reinstall nvidia drivers every few days...? 

Thanks[/QUOTE]
Which method did you use to install the Nvidia driver?

---

### Post by mickutz on 2006-06-28
I think it's one of your methods, exactly the first one, and I read there that these drivers should be reinstalled everytime there's a kernel update. That's why  I'm asking this.

---

### Post by az on 2006-06-28
You can tell synaptic to put a package on hold.  (In terms of apt, it's called pinning)  Just pin the current linux-image-386 package.

Yes, the kernel gets updates and in Warty, it even got a version revision.

---

### Post by tseliot on 2006-06-28
[QUOTE=mickutz]I think it's one of your methods, exactly the first one, and I read there that these drivers should be reinstalled everytime there's a kernel update. That's why  I'm asking this.[/QUOTE]
If you used Method 1 (the driver from the repos) you can make Ubuntu update the restricted modules (automatically) every time the kernel is updated.
Type:
```
uname -r
```
You will get something like 2.6.15-25-**386** or 2.6.15-25-**k7**, etc.

Then install the dummy package:
```
sudo apt-get install linux-386 (or 686 or k7, etc., according to your architecture, which you checked when you typed "uname -r")
```

---

### Post by mickutz on 2006-06-28
OK, tseliot, I think for now I will stick to your advice, because pinning takes a bit of time and it's kind of a complex method. Anyway, I have to try pinning sometime... Thanks

---

