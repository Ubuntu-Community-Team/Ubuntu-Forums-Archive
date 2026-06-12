---
title: "How to add free diskspace to existing pations w/o a CD?"
date: 2009-10-20
forum: Desktop Environments
---

### Post by emptist on 2009-10-20
Hi,

I have some 50G new disk space saved from old Windows partition and want to add them to ubuntu however I have difficulty getting a LiveCD then how can I do this on a running system (safely)? (I know little on this.)
I'd like that /home part could grow to use the space though any approach that such as linking or something that just works will be OK.
I've used up 78% of my home part now with a virtualbox in it.
Thanks in advance.

---

### Post by undecim on 2009-10-20
If you want to expand your current partition, you will need to do it with gparted from a livecd. Most any linux livecd will do this though (or even a thumb drive made with unetbootin, or ubuntu's startup disk creator)

You can still format and mount the old partition somewhere, and store some large files on it. (like your virtualbox disk, for example)

If you need a file to appear in one place while being stored in another, you can create a symbolic link with the command "ln --symbolic real_file link_to_file"

---

### Post by emptist on 2009-10-20
Thanks.

I'll try to format and mount it...well, to which mount point then, is there any thing important?

By the way I am able to boot from a copy of ubuntu CD image located in Windows disk C: and will that work?

I installed my ubuntu this way but I dare not try to resize disk thinking it will then re-install the whole system.

---

### Post by theozzlives on 2009-10-20
How big is your VirtualBox file? You could rename .VirtualBox to .VirtualBack, make your 50 GB partition, then create a new .VirtualBox. Add this line to your fstab:
```
/dev/sda2 /home/*yourusername*/.VirtualBox *filesystemtype* relatime 0 2

```
save, exit, go to Terminal and type:
```
sudo mount -a
```
then just go:
```
sudo mv ~/.VirtualBack/* ~/.VirtualBox/
rm ~/.VirtualBack
```
Your Virtual drives should be on the new 50 GB partition.

---

### Post by Elfy on 2009-10-20
> I installed my ubuntu this way but I dare not try to resize disk thinking it will then re-install the whole system.If you installed ubuntu inside windows then resizing the disk is a bit different I think. If ubuntu is in the windows Add/Remove list then it is Wubi.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by llawwehttam on 2009-10-20
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

and here I am providing a nice link

---

### Post by emptist on 2009-10-20
> **forestpixie said:**
> If you installed ubuntu inside windows then resizing the disk is a bit different I think. If ubuntu is in the windows Add/Remove list then it is Wubi.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)
Thank you. I didn't install in windows I was copying the cd image together with extracted .disk and casper folders to C:  and then with a modified menu.lst I was booting from windows partition C: and installed ubuntu without a Live CD.

---

### Post by emptist on 2009-10-20
thanks I'll try it.

---

### Post by emptist on 2009-10-20
> **theozzlives said:**
> How big is your VirtualBox file? You could rename .VirtualBox to .VirtualBack, make your 50 GB partition, then create a new .VirtualBox. Add this line to your fstab:
```
/dev/sda2 /home/*yourusername*/.VirtualBox *filesystemtype* relatime 0 2

```
save, exit, go to Terminal and type:
```
sudo mount -a
```
then just go:
```
sudo mv ~/.VirtualBack/* ~/.VirtualBox/
rm ~/.VirtualBack
```
Your Virtual drives should be on the new 50 GB partition.

my disk:
___________________________________________
partition..filesystem..unused..mountpoint
/dev/sda1..fat32.......12G...../media/WindowsXP
/dev/sda2..extended
/dev/sda5..fat32.......18G
/dev/sda6..fat32.......23G
/dev/sda7..ntfs........50G (<--free)
/dev/sda8..ext4........7G......./home
/dev/sda9..ext4........53G....../
/dev/sda10.swap
/dev/sda3..ext4................./boot
___________________________________________

The .Virtualbox uses up 22G.

I'm now reading gparted mannual.

So, if I'm to resize /home then boot into gparted, if I'm to format and mount then I need not to boot into gparted but run it in ubuntu, am I right?
And it seems gparted is not able to resize ntfs so the choice should be format and mount?
Should I mount it to any name such as /extra or /home2?

Thanks

---

### Post by Elfy on 2009-10-20
> **emptist said:**
> Thank you. I didn't install in windows I was copying the cd image together with extracted .disk and casper folders to C:  and then with a modified menu.lst I was booting from windows partition C: and installed ubuntu without a Live CD.

Just checking :)

---

