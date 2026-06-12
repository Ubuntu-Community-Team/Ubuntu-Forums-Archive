---
title: "Help needed with data recovery"
date: 2009-02-06
forum: General Help
---

### Post by skywatcher on 2009-02-06
A while ago my Ubuntu 8.10 installation became corrupted, which meant that it wouldn't boot anymore. Fortunately, it was a Vista/Ubuntu dual boot installation done with Wubi, so I could copy my /home directory to a folder on Windows.  This is a file called home.disk located in a folder on /host/Users/...

I have since re-installed Ubuntu 8.10 again using Wubi, and now I would like to get my data back. Is there some way that I can open the home.disk file, either in Ubuntu or in Windows (but preferably in Ubuntu)?

---

### Post by hyper_ch on 2009-02-06
how did you exactely copy it to windows?

---

### Post by caljohnsmith on 2009-02-06
If you boot your Ubuntu Live CD, you should be able to mount and access the home.disk from there. Once you boot the Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is your Vista partition sdaX (like sda2 for example), and then do:
```
sudo mkdir /media/Vista /media/home
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /media/Vista
sudo mount -o loop /media/Vista/host/Users/.../home.disk /media/home
gksudo nautilus /media/home &
```
If you run into any problems, please post the contents of your terminal session where you run all the commands, and we can work from there if you want.

---

### Post by skywatcher on 2009-02-06
Thanks for pointing me in the right direction.

As it turned out, I didn't have to carry out all the steps.  Since a Wubi installation doesn't create a separate partition, all I had to do was the following:

```
sudo mkdir /media/home
cd /host/Users/Chris/Ubuntu_backup/ubuntu/disks (this is where home.disk is located)
sudo mount -o loop home.disk /media/home
```

What a relief to have my data back!

---

