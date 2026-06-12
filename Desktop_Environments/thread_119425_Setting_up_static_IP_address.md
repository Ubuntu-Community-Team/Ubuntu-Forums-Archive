---
title: "Setting up static IP address"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Winux123 on 2006-01-19
Is there a way to setup my network card with root privileges? If i go thru the GUI to get there it is greyed out and instructs me to hit a key or button for administrative privs , but I don't see that button anywhere. Any help would be appreciated:???: 

Thanks

Shawn

---

### Post by geekphreak on 2006-01-19
Open up System -> Networking and try it again.

---

### Post by GeneralZod on 2006-01-19
Try

```

sudo kcontrol

```

The default System Settings does not fully fit on some people's screens, so that they can't see buttons and such,

Also, beware - knetworkconf does *not* save your default gateway due to a silly bug.  If you want to change your gateway, you'll have to manually edit /etc/network/interfaces.

Edit:

For more details, see e.g. [here](http://ubuntuforums.org/showthread.php?t=111956&highlight=gateway+kubuntu).

---

### Post by mips on 2006-01-19
You can also use a key combination to get into admin mode. Unfortunately I cannot remember what the two keys were.

---

### Post by Winux123 on 2006-01-20
Thanks for the help guys.I did end up finding the "administrator mode" button , I had to expand the box down alittle. Not that it made much of a difference , i had to set it up thru the CLI anyway becuase of the "bug" . 

Thanks again:D

---

