---
title: "xserver 10.4 has broken wine and openoffice"
date: 2006-08-24
forum: Desktop Environments
---

### Post by theslut on 2006-08-24
I upgraded to the newest xserver update the other day then read it didn't work, so i followed the lastest instructions on getting 10.4 which was supposed to fix the problem.

I've got no problems entering the desktop but now wine won't run and neither will openoffice.

This is what happens when i run wine.

```

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  78 (X_CreateColormap)
  Value in failed request:  0x0
  Serial number of failed request:  72
  Current serial number in output stream:  9

```

When i run openoffice i get the splash screen then this

```

** (process:5929): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

I can't seem to figure out how to get 10.2 back on before all this crap happend. Can someone help me?

cheers.

---

### Post by FuriousLettuce on 2006-08-24
To rollback to 10.2, do

```
sudo apt-get install sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10.2
```

Then, from the terminal [Alt+F1], login, then do

```
sudo /etc/init.d/gdm restart
```

---

### Post by orb9220 on 2006-08-24
And it is not 10.4 i updated to that skipping 10.3 thankfully and dvdshrink is working find and just loaded up open office word with no problems.

---

### Post by theslut on 2006-08-24
E: Version &#8216;1:1.0.2-0ubuntu10.2&#8217; for &#8216;xserver-xorg-core&#8217; was not found

---

