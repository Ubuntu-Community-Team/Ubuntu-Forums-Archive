---
title: "I can't open Ubuntu after remove passphrase from LUKS"
date: 2013-08-15
forum: Desktop Environments
---

### Post by expertup on 2013-08-15
Hello,


When I have instal new Ubuntu 13.04 64bit, I made encrypt all partition. After some weeks, I wanted to remove password. I found on this page [http://askubuntu.com/a/110195](http://askubuntu.com/a/110195) the command:
```
sudo cryptsetup luksRemoveKey /dev/sda5
```
On My HDD all encypted partition is also on */dev/sda5*. After entering this command, terminal asked me for the current password. After entering the password, I had to confirm the changes. After all these operations, I rebooted the computer.


Since then, I am asked for a password, which I do not know. When I type the old password or leaves the field blank, nothing it does not.

---

