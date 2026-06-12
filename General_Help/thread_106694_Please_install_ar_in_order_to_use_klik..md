---
title: "Please install ar in order to use klik."
date: 2005-12-21
forum: General Help
---

### Post by dajomu on 2005-12-21
This is the message I get trying to install a program using klik (konqueror).

Installed klik by using Alt+F and wget klik.atekon.de/client/install -O -|sh

Anyone knows what this is all about?

DajomU

---

### Post by kambei on 2005-12-21
I have not encountered the error message you noted in your subject line, but I just installed klik this week myself and there were two additional steps I had to perform to get it working.

First check your /etc/fstab file - do you see similar lines like these?:

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

If not, open a terminal and run the following command:

sudo ~/klik-cmg-install-root

Secondly, I needed to install the 'rpm' package to get the rpm2cpio command needed by klik for some of its files. In that same open terminal, run these commands:

sudo apt-get update
sudo apt-get install rpm

I hope that clears up your problem. Good luck!

---

### Post by awakatanka on 2005-12-22
[QUOTE=dajomu]This is the message I get trying to install a program using klik (konqueror).

Installed klik by using Alt+F and wget klik.atekon.de/client/install -O -|sh

Anyone knows what this is all about?

DajomU[/QUOTE]
Use  wget klik.atekon.de/client/install -O -|sh in consule and it will make youre OS klik ready.

---

### Post by dajomu on 2005-12-22
I tried what you guys suggested but it still wont work and I still get the same errormessage.

I tried to  run the command```
wget klik.atekon.de/client/install -O -|sh
```

and then install a klik-program when the konqueror opened up. I then received a message in the konsole saying:
```
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
ASSERT: "!icon.isEmpty()" in /root/3.5/kdebase/kdebase-3.5.0/./libkonq/konq_pixmapprovider.cc (79)
```

DajomU

---

