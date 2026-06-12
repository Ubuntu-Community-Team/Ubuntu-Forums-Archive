---
title: "Swap partition not working, but no notice"
date: 2006-09-02
forum: Desktop Environments
---

### Post by FrederikVds on 2006-09-02
Today I was looking at a performance tweak for Ubuntu involving my swap partition.
While I was checking if this tweak is suitable for me, I noticed something strange.
My swap partition wasn't on! When I tried to turn it on with sudo swapon -a, I got an invalid argument error.
I then used mkswap -c /dev/... and tried doing sudo swapon -a again and it works now. Now my Ubuntu runs so much faster (of course).

How is it possible that I didn't know my only swap partition wasn't working? How is it possible that Ubuntu didn't even give a notice about this on boot-up?

---

### Post by Crooksey on 2006-09-02
If you didnt set u a swap partion during the install,a dn swap isnt listed in /etc/fstab, then there would be no actual erros

```

sudo gedit /etc/fstab
```

Make a new line (replace /dev/sda6 with you swap partition.
```


/dev/sda6       none            swap    sw              0       0

```

---

