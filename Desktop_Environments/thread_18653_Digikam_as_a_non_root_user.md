---
title: "Digikam as a non root user"
date: 2005-03-08
forum: Desktop Environments
---

### Post by mirtux on 2005-03-08
Hi everybody,
  i'm trying to access my Canon Powershot camera with digikam, but i cannot do that unless i'm superuser. I've tried to change write permission of the executable /usr/bin/digikam but nothing has changed. Any ideas?

Thanks for help,
MC

---

### Post by bored2k on 2005-03-08
[QUOTE=mirtux]Hi everybody,
  i'm trying to access my Canon Powershot camera with digikam, but i cannot do that unless i'm superuser. I've tried to change write permission of the executable /usr/bin/digikam but nothing has changed. Any ideas?

Thanks for help,
MC[/QUOTE]
 What if you try to mount it with the umask=000 parameter ?

---

### Post by mirtux on 2005-03-08
I didn't try to do that, but digikam automatically mount the camera after you plug in the usb cable... only as a root user..

MC

---

### Post by bored2k on 2005-03-08
[QUOTE=mirtux]I didn't try to do that, but digikam automatically mount the camera after you plug in the usb cable... only as a root user..

MC[/QUOTE]
 yes that's what it normally does, but if u can find out the /dev/ device it uses u could umount it / mount it with those read/write parameters. I dont kno wich /dev/ it is but it should be a usb device of some sort . 

Once mounted, df -h should show mounted writable discs.


edit >> 4.20am imma go zZzZz so if u were thinking of asking me something for a quick reply ... [A]bort [R]etry [F]ail ... F

---

### Post by mirtux on 2005-03-08
Thanks, this evening i'll have a look and tell the results.
PS: what does it mean umask=000?

Regards,
MC

---

### Post by mirtux on 2005-03-21
[QUOTE=bored2k]yes that's what it normally does, but if u can find out the /dev/ device it uses u could umount it / mount it with those read/write parameters. I dont kno wich /dev/ it is but it should be a usb device of some sort . 

Once mounted, df -h should show mounted writable discs.


edit >> 4.20am imma go zZzZz so if u were thinking of asking me something for a quick reply ... [A]bort [R]etry [F]ail ... F[/QUOTE]
I cannot find it in any position..... or in any sdx devices.... help appreciated, because i don't know how digikam or gtkam works with these usb devices.

Regards,
MC

---

### Post by peculier on 2005-03-24
I had the same problem,
For those still seeking an answer, look here:
[http://www.gphoto.org/doc/manual/permissions-usb.html](http://www.gphoto.org/doc/manual/permissions-usb.html)

---

### Post by mirtux on 2005-03-27
Hi,
   i would like to thank you for the link you submitted since i've managed to have the usb digital camera running as a normal user.

Regards,
MC

---

