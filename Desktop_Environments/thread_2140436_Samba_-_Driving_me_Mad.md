---
title: "Samba - Driving me Mad"
date: 2013-04-29
forum: Desktop Environments
---

### Post by Geffers on 2013-04-29
I have samba working fine on a home network.

Wanted to add my Raspberry Pi to the network so, for test purposes added a VERY SIMPLE config file as shown;

```

[global]
	workgroup = FAIRMEAD 
	null passwords = yes
	encrypt passwords = yes
[R-Pi] 
	comment = For testing only, please
	path = /
	read only = no
	guest ok = yes

```

Worked fine :)

Added a USB stick and coppied above but path was /media/KINGSTON/

Restarted servers and now I get

Failed to mount windows share for the Kingston USB stick.
smb://raspberrypi/r-pi  is a directory.

What on Earth is happening.

Geffers

---

### Post by feffer on 2013-04-29
Samba has given me fits too! I image you've tried connecting the USB stick to a tower or laptop? I know what the Raspberry Pi is, but don't have one. You could also create a directory on it and put a few small files in there and see if you can get that to work on samba. If both of those things work, then the stick should work in the RP. Then other trouble-shooting steps to take.

---

