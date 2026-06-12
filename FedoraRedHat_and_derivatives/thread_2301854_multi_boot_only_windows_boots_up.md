---
title: "multi boot: only windows boots up"
date: 2015-11-05
forum: Fedora/RedHat and derivatives
---

### Post by liron2 on 2015-11-05
so here is the story:

first i had only centos7 and i was thinking about adding windows 7 for a long time now...
recently i installed windows 7 and since then it only booted from windows.
so i searched for a fix and found the:

"
[COLOR=#ff0000]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair[/COLOR]
"

fix which i run from live ubunto cd and its results can be seen here: [http://pastebin.com/2ZCBackh](http://pastebin.com/2ZCBackh)
also tried these:
[COLOR=#ff0000]sudo mount /dev/sda /boot
sudo apt-get update
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo umount /boot[/COLOR]
results: [http://pastebin.com/8bpYXZEB](http://pastebin.com/8bpYXZEB)

in my attempts to set up multi boot i thought why not use clonezilla to fix the boot-loader.
so i used clonezilla to restore 3 of my partitions (im periodicly backing up).
sadly, it didn't work and i got myself a:
[COLOR=#ff0000]error: no such partition.
Entering rescue mode...
grub rescue>[/COLOR]
on startup.

then i fixed my windows with windows 7 installation disk and got back to 'only windows boots now' problem.
searched a little more and got to the option of using boot-repair.
i tried its Recommended repair but it failed and gave me an info link to use when asking on forums.
here is the info: [http://paste.ubuntu.com/13105844/](http://paste.ubuntu.com/13105844/)

im working on this issue alone for a week now and i can sure use some help :(

---

### Post by yancek on 2015-11-05
Use your CentOS installation medium, go to the site below and follow the steps to reinstall Grub2.  You will also need to run grub-mkconfig after which is explained in the second much more detailed second link below.  grub-mkconfig is what is actually run when using update-grub on some systems such as Ubuntu.

[http://luzem.dyndns.org/2014/10/02/centos-7-recover-grub/](http://luzem.dyndns.org/2014/10/02/centos-7-recover-grub/)

---

### Post by liron2 on 2015-11-06
on step 3 i don't have the option to selecet `rescue a Centos system`
so i choose Install CentOS 7 and continue...

i get to the desktop gui and do:

[COLOR=#ff0000]grub2-install –root-directory=/mnt/sysimage/ /dev/sda[/COLOR]

result:
bash: grub-install: command not found...


any use to continue to the grub-mkconfig part?


how can i workaround this?

---

### Post by howefield on 2015-11-06
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by liron2 on 2015-11-06
things i want to point out:

1. present (or backed-up) CentOS7 is an OS i don't want to reinstall or lose (thats why i backed it up using clonezilla) or change partitions size etc...2.[INDENT]a. before attempting to restore my partitions i reinstalled CentOS7 (just to see if it fixes the multi-boot problem, not as a solution)[/INDENT]
[INDENT]b. then i saw i boot only to my newly created CentOS7.[/INDENT]
[INDENT]c. only then i restored my partitions with clonezilla.[/INDENT]

so it sounds like i have two seperate boot partitions:
one that sits on /dev/sda2 (windows boot which is also the current boot device)
second that sits on /dev/sda6 (obviously CentOS boot)

is this normal?

and more important and main question:

how do i solve this to end up with multi-boot? (windows+centos boot menu)

p.s.
maybe some background on my partitions topology before installing windows will help:

name: home
mount point: /home
desired capacity: 76.756GB
device type: LVM
FS: xfs
volume group: cl

name: boot
mount point: /boot
desired capacity: 500MB
device type: standart partition
FS: xfs
(no volume group)

name: root
mount point: /
desired capacity: 51.2GB
device type: LVM
FS: xfs
volume group: cl

name: swap
(no mount point)
desired capacity: 3.856GB
device type: LVM
FS: swap
volume group: cl

---

### Post by Diego_Vega on 2016-02-16
1>backup centos 7 
2>reinstall windows 7
3>when installing windows 7 erase your whole drive
4>Install centos 7 
5>reinstall old information via backup

---

