---
title: "Yet another Windows/grub question."
date: 2009-02-22
forum: General Help
---

### Post by tenmilez on 2009-02-22
I have an asus eee 1000 which has two SSD hard drives, the primary which I have Windows installed on and the secondary which has ubuntu intrepid along with grub. (I use the words primary and secondary loosely. To be more precise, ubuntu refers to the partition with Windows as sda1 and ubuntu as sdb1). My BIOS is set to boot from the secondary drive first so that it hits grub and not Windows. 

My menu.lst looks like this:

```
title		Ubuntu 8.10, kernel 2.6.27-8-eeepc
uuid		0217be39-9416-4434-afbe-9bc277bcf7ff
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=0217be39-9416-4434-afbe-9bc277bcf7ff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-eeepc
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-eeepc (recovery mode)
uuid		0217be39-9416-4434-afbe-9bc277bcf7ff
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=UUID=0217be39-9416-4434-afbe-9bc277bcf7ff ro  single
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		Windows XP Pro
root		(hd1,0)
#savedefault
#makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

It will boot ubuntu and Windows fine so long as there isn't a USB drive plugged in. When there is and I try to boot Windows it looks for it on the USB drive. 

I spent hours and hours last night to get this far while trying to avoid making such a post, but I'm desperate. Thanks in advance.

---

### Post by WatchingThePain on 2009-02-22
Interesting,
What about the option in the bios that says 'boot other device'. Turn that off. Sorry I can't be more specific but I remember that from ages ago.

---

### Post by tenmilez on 2009-02-22
Ah, I didn't realize I could turn off some of those options. All this time I had just been reordering them to fit my needs. Seems like a sketchy way to do it (I think there's probably a 'more right' way to configure grub in my situation), but whatever works works. Thank you.

---

### Post by caljohnsmith on 2009-02-22
You could add an additional entry for Windows in your menu.lst like:
```
title       Windows XP Pro (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then when you have your USB drive plugged in, the above entry should work to boot Windows, assuming the Windows drive is now the 3rd boot drive. Let me know how that goes if you decide to try it.

---

