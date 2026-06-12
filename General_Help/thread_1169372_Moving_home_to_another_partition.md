---
title: "Moving /home to another partition"
date: 2009-05-25
forum: General Help
---

### Post by scaat on 2009-05-25
Hello guys. I am quite a newbie for ubuntu after all those years sticking with Windows based systems. Last week I really get tired to have explorer failures in a fresh installed system. I have wiped out all data on the laptop and installed Ubuntu 9.04. So far, everything is like a dream and my laptop is working like a clock :)

Actually, I am pretty sure that someone has already asked and solved this kind of issue. Despite of all my search attempts, I could not find any info on forums. There are some sites which are explaining how to do this but they are either not clear and explaining enugh for a newbie like me or incomplete (which is the reason I am posting this on here.) 

I have tried to move my /home folder to another partition, because I am installing many vm's on virtual box and holding so many document, I don't want to fill up the system partition with all these. Anyway, I tried to move it by following this howto:

[http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)

clearly, I did something wrong. It was easy enough to create the new partition with gparted but rest is really a mess. I have moved the /home to /home.bak than rest is completely lost for me :) there were problems on login because my /home folder was not where it supposed to be. hopefully, I have managed to get into the recovery mode and move the folder back to its place, /home folder. Lucy for me, system is working fine now but I still couldn't managed to move the /home to its own partition. 

my hdd configuration is like follows:

/dev/sda1       ntfs (vaio recovery)
/dev/sda2       ntfs (vista, don't blame me guys, it is just for the games :)
/dev/sda3 extended
    dev/sda5    ext4 (linux mountpoint:/)
    dev/sda6    swap
/dev/sda4       ext4 (this is where I want /home folder moved to) 

I really will appreciate if someone can lead me how to do this step-by-step. thanks in advance people!

---

### Post by ckonestroh on 2009-05-25
I hate to say this but with all my experience in Linux....

I believe when you install Ubuntu or any linux distro you have to set up separate partitions...

Meaning you have to do a manual install of directories... This is usually safety measure. Administrators use this set up to keep people from accessing data....

hmmm...

good luck...

---

### Post by satnelav on 2009-05-25
I think it is so easy to do now:

1. mount /dev/sda4 using ubuntu graphical interface (so it becomes e.g. /media/disk-1).

2. sudo cp -a /home/* /media/disk-1

3. sudo umount /media/disk-1

4. sudo nano /etc/fstab

add this line at the end:

/dev/sda4 /home ext4 defaults  0  0

5. sudo mv home home.bck

6. sudo mount /home

---

### Post by YldGuy on 2009-05-25
> **scaat said:**
> Hello guys. I am quite a newbie for ubuntu after all those years sticking with Windows based systems. Last week I really get tired to have explorer failures in a fresh installed system. I have wiped out all data on the laptop and installed Ubuntu 9.04. So far, everything is like a dream and my laptop is working like a clock :)

Actually, I am pretty sure that someone has already asked and solved this kind of issue. Despite of all my search attempts, I could not find any info on forums. There are some sites which are explaining how to do this but they are either not clear and explaining enugh for a newbie like me or incomplete (which is the reason I am posting this on here.) 

I have tried to move my /home folder to another partition, because I am installing many vm's on virtual box and holding so many document, I don't want to fill up the system partition with all these. Anyway, I tried to move it by following this howto:

[http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)

clearly, I did something wrong. It was easy enough to create the new partition with gparted but rest is really a mess. I have moved the /home to /home.bak than rest is completely lost for me :) there were problems on login because my /home folder was not where it supposed to be. hopefully, I have managed to get into the recovery mode and move the folder back to its place, /home folder. Lucy for me, system is working fine now but I still couldn't managed to move the /home to its own partition. 

my hdd configuration is like follows:

/dev/sda1       ntfs (vaio recovery)
/dev/sda2       ntfs (vista, don't blame me guys, it is just for the games :)
/dev/sda3 extended
    dev/sda5    ext4 (linux mountpoint:/)
    dev/sda6    swap
/dev/sda4       ext4 (this is where I want /home folder moved to) 

I really will appreciate if someone can lead me how to do this step-by-step. thanks in advance people!

This is what I followed. Works like a dream. [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by scaat on 2009-05-25
> **YldGuy said:**
> This is what I followed. Works like a dream. [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

that worked great, thanks a lot!

and thanks everybody who helped :)

---

