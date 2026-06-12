---
title: "Wammu doesn't communicate with Nokia"
date: 2009-06-23
forum: General Help
---

### Post by Qwerty_ls on 2009-06-23
Hi everybody,
I'm an absolute newbie..
I'm using ubuntu 9.04 and a nokia 6630. Ubuntu recognizes my phone so i can connect to internet just with one click.
I would like to connect to see my contacts, messages and other things just like pcsuite, as well. I've seen the pcsuite doesn't install neither using wine so I've tried wammu kmobiletool and gnooki. Only the first one is able to run the gui appropriately. I managed to connect wammu and nokia thanks to gnapplet over symbian but when i try to retrieve something I get the following message:
"Error while coomunicating with phone
Description: Error writing device
Function: GenNextMemory
Error code:11"

I get the following message on bash when i start wammu:
pacio@pacio:~$ wammu
/usr/lib/python2.6/dist-packages/Wammu/Error.py:27: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Debug log created in temporary file </tmp/wammuDcw5i9.log>. In case of crash please include it in bugreport!

Please can anybody help me?
Thanks in advance

---

### Post by ben2talk on 2009-06-28
Bump.

ben [~] lsusb -v |grep Nokia
Bus 004 Device 004: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent
  idVendor           0x0421 Nokia Mobile Phones
  iManufacturer           1 Nokia
  iProduct                2 Nokia N70

It's there - but I can't access the filesystem.

I'm using Jaunty - need to update my info.

---

