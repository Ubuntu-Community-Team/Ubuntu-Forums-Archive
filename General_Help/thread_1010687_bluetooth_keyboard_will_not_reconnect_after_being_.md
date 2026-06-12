---
title: "bluetooth keyboard will not reconnect after being turned offf"
date: 2008-12-14
forum: General Help
---

### Post by gsrcrxsi on 2008-12-14
ok im having a little trouble after a fresh install. im using a logitech MediaBoard Pro (the PS3 keyboard & touchpad combo).

on my old install, i ran into this issue but i cant remember how i resolved it, and i cant seem to find the how-to that i used before either. 

basically how it worked before (and how i would like it to work again) is for the keyboard to be recognized and turned on at boot, and for it to reconnect when i turn it off and back on again. the KB has a power switch which turns it off and saves battery life. 

not getting it connected was easy, i aquired the MAC address, added it to /etc/bluetooth/hcid.conf
```

device 00:07:61:D2:89:F7 {
name “Logitech MediaBroard Pro”;
auth enable;
encrypt enable;
}

```

and i can start it manually with :
```
sudo hidd --search
```

and ive even gotten it to connect at boot by editing /etc/default/bluetooth with:
```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:02:61:D2:89:F7 --master --server"
```

however the one thing that has been a nuesance (sp?) is that if i turn the KB off and back on, it does not automatically reconnect. it did this before ao i know its possible i just cant remember how i did it. 

any help greatly appreciated :)

---

