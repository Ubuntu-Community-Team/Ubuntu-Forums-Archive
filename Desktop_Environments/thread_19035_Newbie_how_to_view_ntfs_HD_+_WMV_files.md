---
title: "Newbie: how to view ntfs HD + WMV files"
date: 2005-03-10
forum: Desktop Environments
---

### Post by bitsnedker on 2005-03-10
Hi - I'm a "Ubuntu Linux Switcher" from M$ - and I must say that Ubuntu is great - but I still need to work with both platforms (Linux + M$) - and I would like to see my windows disks - I think that I should be able to see the disks when I go to "Computer - disks"  (I have made an dualboot).

I've tried to solve my problem with seeing my ntfs/fat 32 disks by trying to install an package from the "Synaptic packagehandler" - I installed the hfsplus from the "Multiplatform" section - but I can't find the program - how do I activate it - and is it the right program?

I have read that I will never be able to write to an ntfs HD from Linux but I have the read permission - also I have read that with the "old" fat32 than I should have both read/write permission - is that correct? - or must I install some package?

I have som .wmv files (files maked to be viewed in Windows Media Player) - when I try to view them into my totem viewer then I get the message that the .WMV is'nt supported into ubuntu - is it possible to make it viewable - for instance by installing another program?

---

### Post by Buffalo Soldier on 2005-03-10
for mounting NTFS drive -> [http://ubuntuguide.org/index.html#automountntfs](http://ubuntuguide.org/index.html#automountntfs)

read the rest of [http://ubuntuguide.org/](http://ubuntuguide.org/) you'll find many useful things there for beginners

---

### Post by lorap on 2005-03-10
[QUOTE=bitsnedker]Hi - I'm a "Ubuntu Linux Switcher" from M$ - and I must say that Ubuntu is great - but I still need to work with both platforms (Linux + M$) - and I would like to see my windows disks - I think that I should be able to see the disks when I go to "Computer - disks"  (I have made an dualboot).

I've tried to solve my problem with seeing my ntfs/fat 32 disks by trying to install an package from the "Synaptic packagehandler" - I installed the hfsplus from the "Multiplatform" section - but I can't find the program - how do I activate it - and is it the right program?

I have read that I will never be able to write to an ntfs HD from Linux but I have the read permission - also I have read that with the "old" fat32 than I should have both read/write permission - is that correct? - or must I install some package?

I have som .wmv files (files maked to be viewed in Windows Media Player) - when I try to view them into my totem viewer then I get the message that the .WMV is'nt supported into ubuntu - is it possible to make it viewable - for instance by installing another program?[/QUOTE]


hi
you can mount ntfs partition this way:
1.create folder in your user folder, say myfolder;
2.sudo /dev/hda0 /home/username/myfolder -t -o umask=000
that's all, if it wouldn't work for hda0 then try hda1 or even hda2.
to unmount write this:
sudo umount /dev/hda0 -f
remember, being able to unmount, close all subfolders of myfolder and files as well.
pavel
israel

---

### Post by landotter on 2005-03-10
I don't mean to be a wiseguy--but if you want an answer to a question like this quickly, use the search feature at the top of the page and you'll get immediate help--it being a common question. Also search for simple questions like this @ ubuntulinux.org. There are many how-tos there and most are very well written.

I find it strange that people don't use those wonderful resources first.

Btw, all you have to do, if your windows drive is the first of two, is add this line to /etc/ftab:
/dev/hda1 /windows/system ntfs umask=0222 0 0

change "hda1" as needed. ;)

As far as WMV in Totem goes--again do the quick search at ubuntulinux.org and you'll find the easy tutorial.

---

### Post by bored2k on 2005-03-10
[QUOTE=landotter]I don't mean to be a wiseguy--but if you want an answer to a question like this quickly, use the search feature at the top of the page and you'll get immediate help--it being a common question. Also search for simple questions like this @ ubuntulinux.org. There are many how-tos there and most are very well written.

I find it strange that people don't use those wonderful resources first.

Btw, all you have to do, if your windows drive is the first of two, is add this line to /etc/ftab:
/dev/hda1 /windows/system ntfs umask=0222 0 0

change "hda1" as needed. ;)

As far as WMV in Totem goes--again do the quick search at ubuntulinux.org and you'll find the easy tutorial.[/QUOTE]
 Sometimes I think the search button should have a 32size-bold blinking font ;) .

---

### Post by landotter on 2005-03-10
[QUOTE=bored2k]Sometimes I think the search button should have a 32size-bold blinking font ;) .[/QUOTE]
<blink>
Well, it really could be in it's own "frame" with a visible entry field. Right now it's next to invisible.

Other than that, I really like the look and feel of the forums. :)
</blink>

---

