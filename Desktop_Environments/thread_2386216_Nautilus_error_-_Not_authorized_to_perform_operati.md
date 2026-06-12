---
title: "Nautilus error - Not authorized to perform operation (udisks-error-quark, 4)"
date: 2018-03-02
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-03-02
I use usbmount for auto mounting usb drive. But when using nautilus (1:3.18.4.is.3.14) navigate the usb drive trying to format the usb drive. nautilus complains "Not authorized to perform operation (udisks-error-quark, 4)". This looks like mount issue after searching on the internet. But managing to allow my user (u)mount, I add **mount** and **umount** file under **/etc/sudoers.d/** with following contents.

```

<user> <host>=NOPASSWD: /bin/mount
[code]

[code]
<user> <host>=NOPASSWD: /bin/umount
[code]

Also in **/etc/usbmount/usbmount.conf** file, I added attributes 

[code]
FS_MOUNTOPTIONS="uid=<my user account id>,gid=<my user account gid>,umask=022"

```

and retboot. 

But it still complains "Not authorized to perform operation (udisks-error-quark, 4)". Is it possible to configure in allowing my user account to format the usb drive through nautilus? 

Thanks

---

### Post by mc4man on 2018-03-02
In Ubuntu usb drives are mounted on insertion by default so what's the reason for using an app that was last updated in 2011?

---

### Post by jtodd.fr on 2018-03-02
Thanks for pointing out! 

Previously I have a problem that usb didn't get detected/auto-mounted by nautilus so I then installed usbmount (Not sure why at that moment nautilus didn't work). Now removing usbmount fixes the problem. 

Thanks again for the help.

---

