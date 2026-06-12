---
title: "Run webcan in a script"
date: 2009-06-19
forum: General Help
---

### Post by hraposo on 2009-06-19
To make my webcam works, I must run the commands, each time I want execute them:

cd /home/a/microdia 
make 
sudo insmod ./sn9c20x.ko 
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./sn9c20x.ko

There are anibody can make a scritp to run all this all this commands, to execute my webcam???

My webcam is: Canyon CN-WCAMN1

---

### Post by hraposo on 2009-06-19
I can do one that's work, but I must to put de password two times:

```
#!/bin/bash
gksu
cd /home/a/microdia && make
sudo insmod ./sn9c20x.ko 
sudo modprobe videodev
sudo modprobe compat-ioctl32
sudo insmod ./sn9c20x.ko
```

How can help me?
I can not turn off the webcam, I need restart the system...

---

### Post by hraposo on 2009-06-19
How can I stop the webcam. Do you know any command. the kill don't works..

---

### Post by hraposo on 2009-06-19
what I do when I do:

**sudo insmod ./sn9c20x.ko**

is activated a module of kernel.
How I do the reverse???????????????

---

