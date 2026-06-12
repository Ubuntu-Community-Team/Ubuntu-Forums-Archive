---
title: "System Inoperable - Apt-Get not installed"
date: 2009-03-04
forum: General Help
---

### Post by fjr0122 on 2009-03-04
I've been having some really nasty problems with my sister's computer. It is dual boot with edgy and windows xp, and niether OS is working. 

When I try to boot ubuntu. It insists on checking the ext3 root partition, then kicks me to a diagnostic command line. While that is loading it tries to use apt-get and reports "command not found reinstall apt-get by typing "apt install apt-get" (or something really similar to that). Other commands are also MIA (dir, cd, and help all work but not much else). 

My thought on this problem was that I would copy her home directory to my ipod and reinstall using the live cd. But everytime I try to copy that directory I end up with permissions problems. 

So I need to know how to get around the permissions, or alternatively a way to install without wiping the partition (keeping the home dir. in other words). 

I figure once I get ubuntu working again I can load the NTFS drive and route around in my windows to fix that OS as well. But every page I find about loading NTFS drives to read and write is dated 2006 and the repositories they list no longer work. 

So basically I need to copy the home directory or reinstall without touching it, then I need to know how to access a NTFS drive for read and write. 

I thank you guys for your help and my sister does too. (she really needs her computer back so she can work on her spanish)

Thanks...

---

### Post by taurus on 2009-03-04
Which partition you have edgy on?  You need to run fsck when it drops you to a prompt.

Otherwise, you can do that from Ubuntu LiveCD.  Boot with the LiveCD.  Then open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by fjr0122 on 2009-03-04
I won't be in front of the machine till early this morning. But I can go ahead and say the root partition is sda4 the swap is sda2 there is a general info partition in sda3 and the windows (ntfs) partition is sda1.

---

### Post by taurus on 2009-03-04
At the prompt, you can run fsck with

```
fsck /dev/sda4
```
Or from Ubuntu LiveCD, do

```
sudo fsck /dev/sda4
```

---

### Post by fjr0122 on 2009-03-05
Ok....
I just went through a lot of rigamaroll and finally got the filesystem all fixed up. But the when I tried to boot it gets all the way to loading Xorg and then there is a no displays error. 

So I ran a dpkg reconfigure and had Xorg rewrite its setup, well then I got an nvidia driver issue. I finally made the graphical system work by running the dpkg again and setting the video card as vesa. So now I have graphics but for some reason the window manager is missing. But this is good enough that I can copy the home folder like I had wanted to so I can back up all her stuff and then wipe the ubuntu install. (I guess). 

Anyways. 

I still don't see a solution to having the system this screwed up and needing to backup the home folder without running into all those permissions problems, you know from the boot cd or some other resource (even plugging the hd into another system caused endless problems). I know this is a feature of linux (and a good one) but what can we do in these cases? 

Does anyone have a procedure for that? I know I cant be the only one to have run up against this problem. 

(though my problem is solved for now maybe we can help future searchers?...)

---

### Post by markusf21 on 2009-03-05
if you make home a separate partition then you can reinstall without nuking home

---

### Post by fjr0122 on 2009-03-05
Yes. 

When I built this system I was aware of that, and it has another partition. Not sure what happened but it didn't take and then I had /home and /media/sda2 and stuff started piling up in /home in spite of me telling my sister not to do that. :/

Is there a way to set home to /media/sda2 after having had the system installed for a while. (again not info I need but I'm trying to get some help for those following me with the same problem)

And even if there was another partition for /home it still wouldn't belong to the user of the live cd. The permissions would still be in place.....

---

### Post by taurus on 2009-03-05
It depends on what filesystem is /dev/sda2.  If it's ext2/ext3, you could mount it in your $HOME like $HOME/backup.  Then, you can save all your stuff to that directory, $HOME/backup (or ~/backup) which will take up the space on /dev/sda2.

The user on the LiveCD is ubuntu while $HOME belongs to a difference user.  But if you have set $HOME to 755, then you can still access your $HOME on the harddrive via LiveCD.

Otherwise, use

```
gksudo nautilus
```
from the LiveCD to copy your old $HOME to an external drive and when you copy it back after you've reinstalled, you can change the ownership back since technically root is now the owner.

---

