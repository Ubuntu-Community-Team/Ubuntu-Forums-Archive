---
title: "Gimp and Ubuntu 14.10"
date: 2014-11-24
forum: Desktop Environments
---

### Post by Pengwyn44 on 2014-11-24
I have removed Gimp from my original load from DVD and then re-installed it.
The problem is that as soon as it starts it gives the following error message:
"GIMP MESSAGE
Unable to open a test swap file.
To avoid data loss, please check the location and permissions of the swap directory 
defined in your Preferences (currently "/home/bryan/.gimp-2.8")."

The Preferences folder contains a file called "gimpswap.3477".
This file is empty.

I have never had a problem with Gimp before!

Bryan Mitchell

---

### Post by Frogs Hair on 2014-11-24
> I have removed Gimp from my original load from DVD  Please explain , Gimp is available in the software center but, hasn't been included with the ubuntu ISO since 9.10.

---

### Post by Pengwyn44 on 2014-11-25
The DVD was supplied by the Linux Format Magazine issue 192 and Gimp was on it.
That version I removed because it gave the error message using Synaptic to ensure
a complete removal. I then downloaded from the software center. The error message
was the same.

---

### Post by sudodus on 2014-11-25
I would remove gimp again and after that remove the whole .gimp directory from your home directory.

```
rm -r /home/bryan/.gimp-2.8
```

if it does not work, try with sudo

```
rm -r /home/bryan/.gimp-2.8
```

and after that re-install gimp.

I hope it helps :-)

---

### Post by User_Friendly on 2015-08-09
Hey all sorry to grave dig an old SOLVED thread.   I solved this a different way though - I just ran gimp as root "sudo gimp" instead of running it as user, because my user account didn't have permissions to create temporary file in /.gimp-2.8.  Hope that helps anyone else with this same issue :)  -UF

---

