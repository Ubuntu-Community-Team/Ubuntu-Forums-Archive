---
title: "Change encrypted boot prompt"
date: 2009-02-14
forum: General Help
---

### Post by WiseGuy1020 on 2009-02-14
I am running a dual boot Ubuntu 8.10 x64 and 32-bit XP. Both are encrypted. When booting ubuntu asks me for my password to unlock encrypted partition.

But it states /dev/disk/by-uuid/49eb5...(sda3_crypt). instead of just sda3_crypt.

Basically I would like it to look like this: 

[http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png](http://news.softpedia.com/images/extra/LINUX/large/encryptedubuntuseventen-large_034.png)

I have looked at crypttab and /boot/grub/menu.lst and I am not sure what to do. I have a feeling that it is relatively simple, but because I am a recent linux convert(noob), I'm scared of messing up encrypted partitions. 

Any help would greatly be appreciated. 

Thank you.

---

### Post by WiseGuy1020 on 2009-02-19
bump

---

### Post by WiseGuy1020 on 2009-02-19
so much for the "helpful and responsive Ubuntu community"

---

### Post by kanka on 2009-05-04
I was looking for the same tweak, and I couldn't find much about it. I figured out a way to do it, so I'm posting my solution here. It involves editing the initrd of your system, so this tweak is not for the absolute beginner. You've been warned. I did this on Ubuntu 9.04, but I guess it should work on other versions. Last note before getting into it, as it is using initrams-tools, you don't need to worry about kernel upgrades: the modified initrd will be rebuilt at each upgrade.

First of all, you need to extract your initrd:
```
  
  mkdir /tmp/initrd-tmp
  cd /tmp/initrd-tmp
  gzip -dc /boot/initrd.img-2.6.28-11-generic | cpio -id

```
[more info about that here]("https://wiki.ubuntu.com/CustomizeLiveInitrd")

Then
```
gedit scripts/local-top/cryptroot
```

Find the line saying
```
if [ -z "$cryptkeyscript" ]; then
```
On my system (9.04) it's on line 268. 2 lines below, you should find something beginning with
```
cryptkey=
```

That's the prompt showing up at boot time, so modify it to suit your needs. Save, leave gedit. Now you'll need to update your initrd image. In order to do that, you'll need to 
```
sudo cp scripts/local-top/cryptroot /etc/initramfs-tools/scripts/local-top/
```

Before the last step, it could be wise to make a copy of your existing initrd image (we never know); adding an entry to your grub/menu.lst to test your updated initrd image could be a good idea too.

So finally:
```
sudo update-initramfs -u
```

That's it!

---

### Post by unutbu on 2009-05-04
Thank you for this useful information!

---

### Post by WiseGuy1020 on 2009-05-24
Thanks alot. That worked beautifully.

---

