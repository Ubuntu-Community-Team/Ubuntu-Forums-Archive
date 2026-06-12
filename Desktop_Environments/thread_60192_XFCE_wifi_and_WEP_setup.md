---
title: "XFCE wifi and WEP setup"
date: 2005-08-26
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-08-26
I have a machine running Ubuntu and xfce with a really bare system. So bare that I don't have a network-admin anywhere! 
I've just set up WEP on the wireless network, but this machine doesn't connect, and I'm having trouble getting iwconfig to set the WEP. I've tried :

iwconfig ath0 key "##########"

but nothing works. 
Anyone have any great ideas?

---

### Post by nicholaspaul on 2005-09-08
Should i prefix a hex key with $? 
Has anyone any experience using iwconfig? 

HELP!!!

---

### Post by Strider on 2005-09-08
nicholaspaul,

When you enter the enc key using iwconfig, you need to use the following format:

64-bit WEP key:
```

iwconfig ath0 key xxxx-xxxx-xx

```

128-bit WEP key:
iwconfig ath0 key 2174 7832 5528 395a 4a38 4c72 27
```

iwconfig ath0 key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx

```

You can continue with the key if you have higher encryption.  Keep in mind these are HEX and not ASCII format.  Also, read the man page for iwconfig:

```

man iwconfig

```

Good luck.  IM me if you can't get it working.

---

### Post by nicholaspaul on 2005-09-08
I think my problem was that I wasn't using 'sudo' . I managed to find this thread a few minutes ago - 
[http://www.ubuntuforums.org/showthread.php?t=62263&highlight=iwconfig+wep](http://www.ubuntuforums.org/showthread.php?t=62263&highlight=iwconfig+wep)
I then simply entered: 
```
sudo iwconfig ath0 essid mynetwork

sudo iwconfig ath0 key ##########

``` 
Now all is working like magic. 
Thanks for the comments Strider.

---

