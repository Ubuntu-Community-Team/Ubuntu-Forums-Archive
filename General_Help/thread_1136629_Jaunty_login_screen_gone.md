---
title: "Jaunty login screen gone"
date: 2009-04-25
forum: General Help
---

### Post by N_Nick on 2009-04-25
Ok so i wanted to try epidermis, a theme manager but things went wrong.

I started downloading the themes but it was taking too long so i decided to cancel it.  I removed epidermis but when i rebooted this morning i got the original brown ubuntu login screen instead of the Jaunty one. 

I looked under System > Administration > Login Window but the Jaunty login screen is not there.

Any thoughts on getting it back? :-k

---

### Post by soro2005 on 2009-04-25
You could try:
```
sudo apt-get install --reinstall gdm
```
and/or
```
sudo dpkg-reconfigure gdm
```

---

### Post by N_Nick on 2009-04-26
> **soro2005 said:**
> You could try:
```
sudo apt-get install --reinstall gdm
```
and/or
```
sudo dpkg-reconfigure gdm
```

Unfortunately that didnt work, thanks for your reply though.

Are login screens saved as files somewhere so i can copy the Jaunty one from the LiveCD for example?

---

### Post by Legace on 2009-04-26
> **N_Nick said:**
> Are login screens saved as files somewhere so i can copy the Jaunty one from the LiveCD for example?

Place the contents of the attached file into:
/usr/share/gdm/themes

(You need to do this as root. Easy way would be:
Terminal -> type in **sudo nautilus** and press enter, enter password, press enter, extract the attached tar file and place the Human folder in the GDM theme folder)

and it should be back :)

---

### Post by N_Nick on 2009-04-26
> **Legace said:**
> Place the contents of the attached file into:
/usr/share/gdm/themes

(You need to do this as root. Easy way would be:
Terminal -> type in **sudo nautilus** and press enter, enter password, press enter, extract the attached tar file and place the Human folder in the GDM theme folder)

and it should be back :)

Ah thank you very much, that did it :)

Now to find how to mark the thread as solved..

Edit: There we go :)

---

