---
title: "Usability issue with herd 3"
date: 2007-02-02
forum: Development CD/DVD Image Testing
---

### Post by davmor2 on 2007-02-02
When installing herd 3 on a laptop you get 2 almost matching icons of two computer screens one behind the other.  1 is network-manager the other network-monitor now I don't have an issue knowing which is which but some one new to Ubuntu/Linux is going to get confused as hell.  They both have orange triangles with "!" in and they both have network config access.

---

### Post by jerrylamos on 2007-02-02
Yes, on my screen there's two icons, one behind the other, and they both say "no network connection".  What do yours say?

I did a "sudo dhclient" to get an inet address, then Firefox can access ubuntu.com.  And network manager & moniter still say "no network connection". 

If there's no network connection, then how am I making this entry on the forum?!:confused:

---

### Post by pochu on 2007-02-03
Could you please report this in [Launchpad]("https://launchpad.net/ubuntu/+filebug") (if it hasn't been reported yet)?

---

### Post by wpshooter on 2007-02-03
For me the update manager still crashes on Herd 3 just a soon as the CD gets to the desktop,** JUST** like it did on Herd 2 !!!

---

### Post by pochu on 2007-02-03
> **wpshooter said:**
> For me the update manager still crashes on Herd 3 just a soon as the CD gets to the desktop,** JUST** like it did on Herd 2 !!!
wpshooter: I think this has been fixed, but the fix isn't in the herd3 because they fixed it when the isos were done. But you can try this to get the fix, before installing:

"sudo aptitude update && sudo aptitude install gnome-app-install update-manager"


Regards
Pochu

---

### Post by wpshooter on 2007-02-03
This is two commands, correct ???

If this is done before installation, is this fix going to be written to ram ???

Thanks.

---

### Post by pochu on 2007-02-03
> **wpshooter said:**
> This is two commands, correct ???

If this is done before installation, is this fix going to be written to ram ???

Thanks.
But are you having this issue in the LiveCD or once you've installed the system, when you boot up?

If the first, sorry, this won't fix the problem in the LiveCD. However, if you have the second, it will fix it (also running that command in the installed system will fix it).

Regards
Pochu

---

### Post by Henrik on 2007-02-04
Actually, you can install things while running the Live CD as long as they are fairly small and you are not too squeezed for RAM.

It's good for testing things like this :)

---

### Post by davmor2 on 2007-02-04
Reported

---

### Post by pochu on 2007-02-04
[https://launchpad.net/bugs/83330](https://launchpad.net/bugs/83330) ;)

davmor2: please, when you do a report about which we have discussed here, post the link :D

Thanks
Pochu

---

### Post by jerrylamos on 2007-02-04
Herd 3 gets a crash on boot up apparently Add/Remove on 3 systems I've tried.  Well on CD Live Persistent I tried the fix in Post #5 above.  Seems to be a whole potful of code.  

I still got the crash after restarting.

---

### Post by Henrik on 2007-02-05
It's not actually a crash, but an old crash report (included by mistake) that triggers the dialog. It's a known bug, since fixed.

---

### Post by davmor2 on 2007-02-06
Sorry :(

---

### Post by pochu on 2007-02-06
Hey Davmor!

There is no problem, everybody have mistakes ;)
Just, the next time search better first :D

Oh, and you can change your profile to show that you are a Feisty testing user and not an Edgy one ;)

Regards
Pochu

---

### Post by davmor2 on 2007-02-09
> **pochu said:**
> Hey Davmor!


Oh, and you can change your profile to show that you are a Feisty testing user and not an Edgy one ;)

Regards
Pochu

Done :lolflag:

---

