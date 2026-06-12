---
title: "Enabling Num Lock on Startup?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by CybaCowboy on 2006-06-03
Previously when my system was running Ubuntu 5.10 ("Breezy Badger"), I had a program installed that caused the Num Lock to be enabled on startup (I can't remember the name of the program anymore though)...

The problem is, after upgrading to Ubuntu 6.06 ("Dapper Drake"), this is no longer the case - the Num Lock is now *off* by default when I boot into Ubuntu!

Any idea how I can have the Num Lock *on* by default when I boot into Ubuntu 6.06 ("Dapper Drake")?

---

### Post by transactionlogfiller on 2006-06-03
sudo apt-get install numlockx, or use synaptic.

---

### Post by ebash on 2006-06-03
If you are using GDM to login and you will like to have numlock on at the login screen (useful when dealing with passwords that include numbers) then make sure that the file 
/etc/X11/gdm/Init/Default ends with:

```

# Set Num Lock
if [ -x /usr/bin/numlockx ]; then
    /usr/bin/numlockx on
fi

exit 0

```

---

### Post by CybaCowboy on 2006-06-03
[QUOTE=ebash]```

# Set Num Lock
if [ -x /usr/bin/numlockx ]; then
    /usr/bin/numlockx on
fi

exit 0

```[/QUOTE]

Worked like a charm!

Thanks.

---

