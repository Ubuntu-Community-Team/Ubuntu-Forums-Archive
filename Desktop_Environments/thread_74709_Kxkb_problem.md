---
title: "Kxkb problem"
date: 2005-10-12
forum: Desktop Environments
---

### Post by abominable on 2005-10-12
I tried to add an extra layout for my keyboard but I got this message:

Will not save configuration

Configuration file "/home/abominable/.kde/share/config/kxkbrc" not writable.

Please contact your system administrator.

I opened kcontrol through root terminal..

I also opened kxkxbrc with kwrite and there was written:


[Layout]
Additional=el
EnableXkbOptions=true
Includes=
Layout=us
Model=
Options=grp:alt_shift_toggle
ResetOldOptions=true
ShowFlag=true
ShowSingle=false
StickySwitching=false
StickySwitchingDepth=1
SwitchMode=Global
Use=true
Variants=

_________________________________________________________________

What should I do ?

---

### Post by adwait on 2005-10-12
```
sudo chmod +rw /home/abominable/.kde/share/config/kxkbrc 
```

Try that.....

---

### Post by abominable on 2005-10-12
I did it and I had the same result.

However permissions from :
-rw-------
changed to:
-rw-r--r--

---

### Post by adwait on 2005-10-12
Ok maybe you can try this:
```
sudo  chmod 777 /home/abominable/.kde/share/config/kxkbrc
```

EDIT: I HAVE BEEN TOLD THAT IT IS BAD PRACTICE TO SET ANYTHING TO 777, SO TRY IT OUT TO ONLY SEE IF IT WORKS.....

---

