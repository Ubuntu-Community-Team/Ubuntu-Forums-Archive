---
title: "bluetooth: class number ?"
date: 2005-12-07
forum: General Help
---

### Post by santo on 2005-12-07
Suddenly I got this popup after login.

Any ideas what it means and if I should make the modifications suggested ?
In contrast to what the popup is telling me, I don't see any 0x0 class entries in that file:
```

user1@laptop01:~$ grep -i class /etc/bluetooth/hcid.conf
        # Local device class
        class 0x3e0100;

```

---

### Post by ltmon on 2005-12-07
I've always used "class 0xff0100;" which supports just about anything (I've used it with hands free mics, phones and input devices).

L.

---

### Post by santo on 2005-12-08
ok, thanx.
I made a copy of the original file and modified the class to 0xff0100
Not sure what it's supposed to do though.

---

### Post by ltmon on 2005-12-08
[QUOTE=santo]ok, thanx.
I made a copy of the original file and modified the class to 0xff0100
Not sure what it's supposed to do though.[/QUOTE]

It indicates the class of your device (i.e. your computer).  This class number gives connecting devices some idea of what the capabilities of your computer are without having to do a full scan of the capabilities list.

The number I gave you sets your computer to "Miscellaneous Computing Device" or something like that, so connecting devices assume it can do pretty much anything.

The popup warning you were getting was saying that your class was set to something fairly restrictive, which may cause _some_ (not all) connecting devices to assume that your computer doesn't have a capability that it does actually have.

L.

---

### Post by santo on 2005-12-09
Great, that makes it a lot more understandable for me :cool: 

Thanx again

---

