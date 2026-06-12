---
title: "creating new home partition"
date: 2009-03-06
forum: General Help
---

### Post by glendavee on 2009-03-06
Apologies for a very basic question. I'm planning to move my /home directory to a new partition by following these directions 

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

My question. Do I quit the live cd and reboot before the step "using the new partition", or do I continue the process of mounting the new partition and moving the directory while running the live cd?

thanks

---

### Post by kanikilu on 2009-03-06
Still on the live CD. It says to reboot further down in the instructions.

---

### Post by mªrty on 2009-03-06
great guide. i used it on my own installation not long ago :)

---

### Post by glendavee on 2009-03-06
Thanks for the help.

---

### Post by glendavee on 2009-03-06
I followed instructions and all seemed to go ok, until the reboot. System seems to be totally screwed. When I boot, all goes ok until the login screen. After logging in, I get an error message "your home directory is /home/david but it does not seem to exist. Do you want to log in with /root as home?" When I select ok, I get further error messages, and eventually the ibex screen with nothing else - no tool bar, nothing. I've tried the recovery process using the live cd as described, but get the same results.
Is there any hope of recovery, or have I just destroyed my file system??

---

### Post by ponyexpress on 2009-03-06
can you login on a virtual terminal?

---

### Post by glendavee on 2009-03-07
How do I do that?

---

### Post by glendavee on 2009-03-07
More info. When I boot using live disk, I can mount the new partition and read the files. Home and home_backup are both on the new partition. Why doesn't this happen on a normal boot?

---

### Post by glendavee on 2009-03-07
Yet more info. I can mount the new partition (/dev/sbd3), but when I mount the old partition(/dev/sbd1), it seems to mount, but I can't open the drive - error message "no mount object for mounted volume". Only contents seem to be a folder called lost+found.
sudo fdisk -l shows all the partitions on the disk ie 
/dev/sbd1
/dev/sbd2
/dev/sbd3
/dev/sbd5

---

### Post by ponyexpress on 2009-03-09
> **glendavee said:**
> How do I do that?

Hold the ctrl + alt keys along with F1 through F6.
You will need to use ctrl+alt+F7 to renurn to your desktop.

---

### Post by glendavee on 2009-03-15
Sorry for long delay - been away.
Not sure I understand. When I ctrl+alt+F1, I get a prompt 

ubuntu@ubuntu:~$

what do I do next??

---

