---
title: "how to configure bluetooth headphone bh200 in hardy."
date: 2008-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by papuaq on 2008-05-23
hello all, I am trying to install my bluetooth headphone in hardy. please give me some idea to proceed. I have installed it successfully in 7.10, but have no idea how. Need proper way to do that. 
Thanks in advance.

---

### Post by papuaq on 2008-05-25
please help.

---

### Post by Keyper7 on 2008-05-26
What do you mean, "no idea how"? In 7.10 it worked out of the box?

---

### Post by papuaq on 2008-05-26
ya, that's what i am saying. It working fine with 7.10. But I don't know, how i have configured it. Can  you please give me step by step way, how to configure it in hardy.

---

### Post by groovete on 2008-05-26
Same problem here (Dell Inspirion 1720, Dell bluetooth headset bh200).
Worked in Gutsy using this howto: 
[http://doc.ubuntu-fr.org/oreillette_bluetooth](http://doc.ubuntu-fr.org/oreillette_bluetooth)
Now in Hardy I get this error message: 
```
xxx@xxxxx:~$ btsco -v 00:16:44:20:93:13
btsco v0.42
Device is 1:0
Error: btsco open (1-0): No such device or address
```
Same error when I try this howto:
[http://wiki.ubuntuusers.de/Bluetooth_Headset](http://wiki.ubuntuusers.de/Bluetooth_Headset)
```

cat /proc/asound/cards
``` 
gives:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel a 0xfebfc000 irq 20
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1
```

I tried it with Blueman Bluetooth Manager, no success.

Any idea? Thanks in advance!

---

### Post by nonducor on 2008-06-07
I had the same problem, but in the newest kernel update in Hardy  (2.6.24-19) it is working just right!

---

### Post by brucebertrand on 2008-06-13
Using 2.6.24-19-rt and I'm still seeing this problem.

---

