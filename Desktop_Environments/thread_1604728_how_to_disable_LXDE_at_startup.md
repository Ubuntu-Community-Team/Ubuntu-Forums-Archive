---
title: "how to disable LXDE at startup ?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by ghat on 2010-10-24
hi

I installed the maverick server, and tightvncserver. I wanted a light desktop environment so I installed lxde. I am running this on a KVM virtual machine.. 

I want the KVM console to fall to text as the default ubuntu-server does, however after installing lxde it seems to start lxdm from somewhere... 

It is disabled in the rc.*/* setup...

```

root@srv:/etc# ls -ld rc.*/*lx* init.d/*lx*
ls: cannot access rc.*/*lx*: No such file or directory
lrwxrwxrwx 1 root root 21 2010-10-24 07:47 init.d/lxdm -> /lib/init/upstart-job
root@srv:/etc# 

```I have no clue where is it starting from can anyone help me disable it ?

G

---

### Post by cavalier911 on 2010-10-24
Disable an upstart service:change the job filename by appending with .nostart,
```
sudo mv /etc/init/lxdm.conf /etc/init/lxdm.conf.nostart
```
Re-enable:rename then start:
```
sudo mv /etc/init/lxdm.conf.nostart /etc/init/lxdm.conf
```
```
sudo service lxdm start
```

---

### Post by RPMurph on 2011-07-12
I moved the file so LXDM stops starting, but when I start the computer it still defaults to terminal 7.  Is there a way to get it to stay on terminal 1?

---

### Post by ghat on 2011-07-22
hi 

in the file 

/etc/grub.d/10_linux

look for the following line...

```

GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=1"

```the default there is vt.handoff=7, change that to 1 and then run 

```

update-grub
sync
reboot

```Ghat
PS: Another thing I have found helpful if you are running in a KVM
is add a 
```

touch /forcefsck 

```in /etc/rc.local, that way if the machine crashes for some reason, it will always do a
fsck on boot-up and be up all the time.. 
I used to be a qemu-nbd regular, before I did that!!!

---

