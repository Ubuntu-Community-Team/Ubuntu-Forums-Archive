---
title: "format"
date: 2009-03-01
forum: General Help
---

### Post by i.arnav on 2009-03-01
Please tell me how to format a pen drive in ubuntu using terminal 

Also to format some other hard drive

---

### Post by taurus on 2009-03-01
What filesystem do you want to format the drive to?  What is the name of the device (/dev/sdb1, etc.)?

```
sudo fdisk -l
```

---

### Post by i.arnav on 2009-03-01
sir i am just new to ubuntu from windows so i dint get you


"sudo fdisk -l" will do ?

---

### Post by i.arnav on 2009-03-01
Fat 32

---

### Post by chriskin on 2009-03-01
might i ask why you Need to format it using the terminal?
get gparted from synaptic and do it from there easily with a GUI

after all, if you are a new user coming from windows, it would be easier if you did it that way wouldn't it?it's all something like three clicks and the drive is formatted. 


(what he meant was to write that command in the terminal and post here what came from it, so he can give you the command you will need)

---

### Post by i.arnav on 2009-03-02
thanx it wrked

---

