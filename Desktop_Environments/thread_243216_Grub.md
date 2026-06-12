---
title: "Grub"
date: 2006-08-24
forum: Desktop Environments
---

### Post by moondogie on 2006-08-24
Help .I have pull-out drives on my pc and when I switched back to Ubuntu 6.06 all I get after the boot sequence is GRUB and a cursor . The drive won't boot intoo the start-up sequence .
Is there a way to get the boot sequence to start ?
I really don't want to reformatt the drive  .
Moondogie](*,)

---

### Post by Iarwain ben-adar on 2006-08-24
Hi,
yes there is a way (actually more than one :D )

1) plug in your drives. (most simple solution i think)

2) boot via live-cd.
```
sudo grub    #let's look where your current root partition is by starting the grub editor
grub> find /boot/grub/stage1     #remember the output of this command,
#beacause it shows where your root partition is.
grub> quit     #quits grub
sudo fdisk -l    #shows the partitions, you have to look for a 'linux' one
sudo mkdir /rec    #for the simplicity, rec stands for recovery
sudo mount -t ext3 /dev/hXX /rec     #hXX stands for the linux partition.
sudo gedit /rec/boot/grubmenu.lst
```

And there you have to change these options...
```

<snip>

title		Ubuntu, kernel 2.6.15-26-386
root		([COLOR="Red"]hd0,5[/COLOR])
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/[COLOR="Red"]hdc6[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

<snip>

```


Then you save the file, and reboot.
Normally it should boot your Ubuntu back =)


Iarwain

---

