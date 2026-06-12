---
title: "Help uninstalling netbook remix"
date: 2009-05-07
forum: General Help
---

### Post by squizz0r on 2009-05-07
Hey all!

I am new to linux and here so go easy on me ;)

Ive recently bought a samsung nc10 netbook and installed the netbook remix on a seperate partition to my windows partition.

I want to remove ubuntu (sorry guys!) just for the time being.

How would I go about removing ubuntu and grub without messing up my windows partition?

Thanks :)

---

### Post by Brandon Williams on 2009-05-07
If you have a USB key with ubuntu on it, try installing mbr to the master boot record to see whether you can boot windows without grub installed in the master boot record.

```
$ sudo install-mbr */dev/sda*
```

Replace /dev/sda with the device name of your primary HDD (it probably is /dev/sda, but double check first).

After running this command in ubuntu, reboot and see if the system boots into windows. mbr automatically boots into the lowest numbered bootable partition, so if that is not your windows partition, then this will not work. However, if it does work, then you can safely remove the Ubuntu partition (I can't understand why you would want to do that, though :-)

If the above doesn't work to boot into windows, then boot from your usb stick and run this command to restore grub so that at least you can boot into ubuntu again.

```
$ sudo install-grub /dev/sda
```

---

