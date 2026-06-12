---
title: "[SOLVED] writing the right entry in /boot/grub/menu.lst"
date: 2008-12-12
forum: General Help
---

### Post by rixtr66 on 2008-12-12
Hey all,cant help but play with other linux distros:-$
anyway i installed slackware 12.2 to /dev/sda3 with the swap on /dev/sda5.
ubuntu is installed on /dev/sda1,i dont know what happened to /dev/sda2 ?
now ive done this before but for the life of me i cant remember how :oops:
here is what i have in /boot/grub/menu.lst

```
#Linux installation on /dev/sda3

title           Slackware 12.2
root            (hd0,1)
makeactive
 chainloader	+1
```
is this even remotely close?cause it doesnt work?
any help would be appreciated!!!
thanks!
Rick

---

### Post by 2hot6ft2 on 2008-12-12
> **rixtr66 said:**
> Hey all,cant help but play with other linux distros:-$
anyway i installed slackware 12.2 to /dev/sda3 with the swap on /dev/sda5.
ubuntu is installed on /dev/sda1,i dont know what happened to /dev/sda2 ?
now ive done this before but for the life of me i cant remember how :oops:
here is what i have in /boot/grub/menu.lst

```
#Linux installation on /dev/sda3

title           Slackware 12.2
root            (hd0,1)
makeactive
 chainloader	+1
```
is this even remotely close?cause it doesnt work?
any help would be appreciated!!!
thanks!
Rick
I may be wrong but if it's sda3 then wouldn't that be (hd0,[COLOR="SeaGreen"]2[/COLOR])

---

### Post by tgalati4 on 2008-12-12
When the grub menu comes up, hit "c" to get to the grub command line:

>root

(hd0,1)

>root (hd0,2)

Found linux partition (or something to that effect)

>chainloader +1

>boot

---

### Post by rixtr66 on 2008-12-12
hmmmmmm....well...thats pretty simple,i'll give it a go!
Thanks!
Rick#-o

---

### Post by TeXtonyx on 2008-12-13
Your grub entry was set up for sda2 = (hd0,1)

So if the fix offered doesn't work, try
sudo fdisk -l (small L)
and it will report your partitions.

---

### Post by rixtr66 on 2008-12-13
ok that fixed the problem with slackware!im also running another linux on my usb hd,and i need to get into it and increase the timeout to 10 sec.
i tried mnt but that didnt work?so how do i access the drive /dev/sdb1
and get into the lilo conf?it starts fine but has a kernel panick,do to not enough time for the hd to initialize.it also has an initrd.but in the grub menu.lst i have it set up the same as slackware except root is(hd1,0)
anyway should i start another thread on this?
thanks
Rick

---

