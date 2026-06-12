---
title: "Huge IO performance difference between /dev/X and /dev/mapper/X"
date: 2009-01-19
forum: General Help
---

### Post by malfist on 2009-01-19
I am trying to figure out I have such slow IO performance and I was using hdparm to check the speeds out and I found something very interesting.

If I do hdparm on /dev/sda the IO speed is as expected, however if I do it through the /dev/mapper/truecrypt1 the speed is a half of the expected speed.

Here are two examples from my harddrives:
```

jerome@ubuntu-desktop:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   3498 MB in  2.00 seconds = 1748.93 MB/sec
 Timing buffered disk reads:  250 MB in  3.01 seconds =  83.13 MB/sec
jerome@ubuntu-desktop:~$ sudo hdparm -Tt /dev/mapper/truecrypt1

/dev/mapper/truecrypt1:
 Timing cached reads:   3444 MB in  2.00 seconds = 1722.33 MB/sec
 Timing buffered disk reads:  120 MB in  3.01 seconds =  39.88 MB/sec

```

And my other HHD:
```

jerome@ubuntu-desktop:~$ sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   3436 MB in  2.00 seconds = 1718.14 MB/sec
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.59 MB/sec
jerome@ubuntu-desktop:~$ sudo hdparm -Tt /dev/mapper/ubuntu--desktop-root 

/dev/mapper/ubuntu--desktop-root:
 Timing cached reads:   3452 MB in  2.00 seconds = 1726.51 MB/sec
 Timing buffered disk reads:   92 MB in  3.07 seconds =  29.98 MB/sec

```

Any idea how to fix this? Or why it's happening?

---

### Post by mikewhatever on 2009-01-19
Isn't it a trade of for using encryption?

---

### Post by hyper_ch on 2009-01-19
when using encryption every little bit will be encrypted and that takes cpu :) it's to be expected that encryption is on large read/write operations slower.

---

### Post by malfist on 2009-01-19
Encryption only has very slight performance penalty. As in a 1-5 MB/s. Even using the test on /dev/sda still useds the encryption, because it's the same device. And besides, I'm running with a quad core.

The issue seems to be with LVM, not dm-crypt or truecrypt.

---

### Post by hyper_ch on 2009-01-19
encryption has the effect that everyting read from and written to a device will be encrypted and with you start copying massive files you'll notice that - I don't think multicores have a positive effect on the encryption as it's done file by file.

---

### Post by malfist on 2009-01-19
The file size remain essentially the same on transfers, and the CPU does matter, what do you think encrypts/decrypts it and/or generates the random numbers? Having more speed means the difference is less. According to benchmarks, the difference between encryped and non-encrypted file systems is less than 10MB/s and I'm seening a difference of 50% that has nothing to do with the encryption. If it was the encryption it would effect the tests on /dev/sda too and I wouldn't notice. It seems through my googling that it's caused by the LVM because it happens randomly when it is used with/without encryption. I am just asking how to fix it.

---

### Post by hyper_ch on 2009-01-20
it depends... on a 1.8ghz the performance penalty can be up to 50% - depending on the caching...

---

### Post by malfist on 2009-01-20
But a 2.5 GHz Quad is slightly different than a 1.8 single core. But still. If it was the encryption it would effect it no matter where I tried to test, /dev/mapper/x or /dev/x. However it is only effecting /dev/mapper/x.

---

### Post by hyper_ch on 2009-01-20
as you said "slightly" different ;)

---

