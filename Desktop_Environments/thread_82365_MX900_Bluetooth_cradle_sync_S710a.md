---
title: "MX900 Bluetooth cradle sync S710a"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Sn1pe on 2005-10-26
I'm trying to figure out any way to sync a Sony S710a with my linux desktop.  I have a Logitech MX900, and the cradle is supposed to give my desktop bluetooth, but I cannot figure out how to get the OS to recognize the cradle as a bluetooth adapter.  Any help would be great.

---

### Post by damien82 on 2005-12-18
i'm having the exact same problem with my mx900, hopefully someone knows what to do

---

### Post by fanoodlehey on 2006-01-06
Me too. I can't get my MX900 cradle to act as a bluetooth hub. I've read and tried lots of stuff but I just can't get it to work.

---

### Post by fanoodlehey on 2006-01-07
Here's some new information. By editing my /etc/bluetooth/hcid.conf file and doing as root
```

hid2hci
hcid
sdpd

```
I can get my logitech cradle to be recognised as a bluetooth adapter. It picks up my keyboard, mouse and even my sony ericsson k700i. However even though the mouse can be seen in "hcitool scan" it does not work and I cannot use it.

Do I need to edit my Xorg.conf file? If so can anyone tell me what to put in it. I'm really trying to learn here but there is only so far you can go with google searches and no experience with this sort of thing.

---

