---
title: "i dont want to give 8gb to ubuntu"
date: 2009-01-12
forum: General Help
---

### Post by erdal123 on 2009-01-12
ubuntu took my 8 gb hardspace, i dont want that i didnt know that ubuntu was going to make a seperate partition  

my question is how can i take 6 gb of ubuntu and give it back to windows c:/

---

### Post by taurus on 2009-01-12
You can't since Ubuntu needs at least 2.5GB (more like a little over 3GB).

---

### Post by erdal123 on 2009-01-12
> **taurus said:**
> You can't since Ubuntu needs at least 2.5GB (more like a little over 3GB).

thats fine with me

how can i sett it to 3 gb

 thanks :)

---

### Post by cb34 on 2009-01-12
gparted

---

### Post by sendblink23 on 2009-01-12
> **erdal123 said:**
> thats fine with me

how can i sett it to 3 gb

 thanks :)

Didn't you get the choice.. of choosing the Ubuntu's Partition,  when installing it as normally?


Oh well head to Gparted with the LiveCD, in the TOP MENU click on Systems, inside Administration or Preferences you should read in one of those Gparted.

Inside there you can Resize & create any partitions.

Be quite careful with playing with it.

---

### Post by erdal123 on 2009-01-12
> **sendblink23 said:**
> Didn't you get the choice.. of choosing the Ubuntu's Partition,  when installing it as normally?


Oh well head to Gparted with the LiveCD, in the TOP MENU click on Systems, inside Administration or Preferences you should read in one of those Gparted.

Inside there you can Resize & create any partitions.

Be quite careful with playing with it.

i thought i could acces ubuntu files in windows, so for instance when i download a song in ubuntu i could open it in windows to,isnt that the case?   thats my problem

i dont have a livecd, i installed ubuntu with a iso file

---

### Post by hyperdude111 on 2009-01-12
It will be almost pointless to have 3 gb to ubuntu. You wont be able to install many apps or use any multimedia. You would be better off using ubuntu of a usb if you are low on space because with only 3 gig all you can do is use the pre-installed apps and look at the desktop.

---

### Post by taurus on 2009-01-12
> **erdal123 said:**
> i thought i could acces ubuntu files in windows, so for instance when i download a song in ubuntu i could open it in windows to,isnt that the case?   thats my problem

i dont have a livecd, i installed ubuntu with a iso file

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sendblink23 on 2009-01-12
sorry erased I was confused of my answer

---

### Post by erdal123 on 2009-01-12
> **sendblink23 said:**
> sorry erased I was confused of my answer

you didnt get my question..

1.
i know how to acces from ubuntu to windows

i want to acces windows to ubuntu! thats the whole problem

2. (secondly not so importent)
im only able to acces(in ubuntu) my H:/ windows drive and not C:/
for some strange reason

---

### Post by sendblink23 on 2009-01-12
> **erdal123 said:**
> you didnt get my question..

1.
i know how to acces from ubuntu to windows

i want to acces windows to ubuntu! thats the whole problem

2. (secondly not so importent)
im only able to acces(in ubuntu) my H:/ windows drive and not C:/
for some strange reason



I Erased my Answer since  Tauros gave you the solution to your answer,  head into that website he gave you.. and download it through inside Windows, and you would be able to do exactly that.. access  *Ubuntu files from inside Windows

---

### Post by cb34 on 2009-01-12
follow post #8.. it's because of the file system type.. like ntfs, ext3..

win and ubuntu dont use the same file system type.. even though you can make them the same when you install everything.. but that's why just for your information.

---

### Post by ugm6hr on 2009-01-12
> **erdal123 said:**
> 
1. i want to acces windows to ubuntu! thats the whole problem

2. im only able to acces(in ubuntu) my H:/ windows drive and not C:/
for some strange reason

1. [http://fs-driver.org/](http://fs-driver.org/)

2. ```
sudo apt-get ntfs-config
```

---

### Post by erdal123 on 2009-01-12
> **ugm6hr said:**
> 1. [http://fs-driver.org/](http://fs-driver.org/)

2. ```
sudo apt-get ntfs-config
```

thank you so much for your support

you guys are great

im getting sentimental :p

---

