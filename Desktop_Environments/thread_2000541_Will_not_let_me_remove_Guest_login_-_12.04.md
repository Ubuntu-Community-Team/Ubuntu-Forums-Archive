---
title: "Will not let me remove Guest login - 12.04"
date: 2012-06-09
forum: Desktop Environments
---

### Post by DS McGuire on 2012-06-09
I really hope somebody can help me with this; I am trying to remove the guest login from lightdm in Lubuntu 12.04. I went to etc/lightdm/ and edited the file lightdm.conf 

I added:

allow=guest=false

to the last line of the file and tried to save it but when I do I get a "Can't open file to write"error.

Any ideas on why this is happening? 

Thanks :)

---

### Post by wilee-nilee on 2012-06-09
> **DS McGuire said:**
> I really hope somebody can help me with this; I am trying to remove the guest login from lightdm in Lubuntu 12.04. I went to etc/lightdm/ and edited the file lightdm.conf 

I added:

allow=guest=false

to the last line of the file and tried to save it but when I do I get a "Can't open file to write"error.

Any ideas on why this is happening? 

Thanks :)

Did you open it with this command.
gksudo gedit /etc/lightdm/lightdm.conf

[http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)

---

### Post by DS McGuire on 2012-06-09
> **wilee-nilee said:**
> Did you open it with this command.
gksudo gedit /etc/lightdm/lightdm.conf

[http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)

I get "gtk-Message: Failed to load module "canberra-gtk-module""when I tried the above code :S

---

### Post by wilee-nilee on 2012-06-09
> **DS McGuire said:**
> I get "gtk-Message: Failed to load module "canberra-gtk-module""when I tried the above code :S

I would check the web with that error.

But you could just gksudo nautilus I suspect navigate to and open that file from there and add the stanza and save it.

---

### Post by lokihound on 2012-09-29
I'm having the same problem.  I opened it in the leaf something.  I'm lost now.

---

### Post by bobblex on 2013-04-06
> **DS McGuire said:**
> I really hope somebody can help me with this; I am trying to remove the guest login from lightdm in Lubuntu 12.04. I went to etc/lightdm/ and edited the file lightdm.conf 

I added:

allow=guest=false

to the last line of the file and tried to save it but when I do I get a "Can't open file to write"error.

Any ideas on why this is happening? 

Thanks :)

If you edited lightdm.conf with the line as you show it, it won't work.
it needs to be:  allow-guest=false

use a dash between allow and guest rather than an equals

Bob

---

### Post by Rex Bouwense on 2013-04-06
See
[http://ubuntuforums.org/showthread.php?t=2132448](http://ubuntuforums.org/showthread.php?t=2132448)

---

