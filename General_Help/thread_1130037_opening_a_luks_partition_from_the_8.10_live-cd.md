---
title: "opening a luks partition from the 8.10 live-cd"
date: 2009-04-19
forum: General Help
---

### Post by googlorenz on 2009-04-19
hello,

i wanted to mount a luks-encrypted partition using the live-cd:
so i used
```
sudo apt-get update && sudo apt-get install cryptsetup
```
to install cryptsetup.

then i checked whether my partition (/dev/sda5) really was a luks partition using
```
sudo cryptsetup luksDump /dev/sda5
```
and got:
```
LUKS header information for /dev/sda5

Version:       	1
Cipher name:   	twofish
...
Key Slot 0: ENABLED
...
Key Slot 7: DISABLED
```
therefore /dev/sda5 clearly is recognized as a luks-partition.

however, when i try
```
sudo cryptsetup luksOpen /dev/sda5 encrypted_sda5
```
and enter the correct(!) password, i get:
```
Command failed: No key available with this passphrase.

```

but, i know that the password is correct, as ubuntu is installed on it, and during boot i can mount it using the same password. however, for some reason i cannot access it from the live-cd.

any help would be appreciated.

googlorenz

---

### Post by googlorenz on 2009-04-19
*push*

any ideas?

---

### Post by shaggy999 on 2009-04-20
Does installing cryptsetup automatically load the proper crypto modules? I think you need to manually load in the twofish crypto module. Check by using the lsmod program, perhaps grepping for 'crypto'.

---

### Post by shaggy999 on 2009-04-20
Ok, so try this:

```
sudo modprobe dm-crypt
```

after installing cryptsetup. That should get the crypto module loaded for mounting a partition. Then continue on with the rest of your commands.

---

