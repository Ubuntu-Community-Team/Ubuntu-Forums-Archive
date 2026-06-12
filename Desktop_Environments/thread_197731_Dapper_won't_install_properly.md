---
title: "Dapper won't install properly"
date: 2006-06-16
forum: Desktop Environments
---

### Post by starNIX on 2006-06-16
So after 3 trys it just won't go.  It looks like it isn't installing grub due to the server being down.  How do I get around this?  Everytime I install,  I get "Error loading Operating system"

---

### Post by localzuk on 2006-06-16
What do you mean 'due to the server being down'?

How are you installing?

---

### Post by starNIX on 2006-06-16
Well,  I used the live CD but that for some reason doesn't install grub so I tried booting from the cd and chroot'ing into the new install and using apt to install it.  Neither way works....  Plz help.....

---

### Post by xenblend on 2006-06-16
Hop into a console window and do 'mkfs -t <ext2/3> /dev/hda1' then do a 'grub-install' on /hda1.

---

### Post by brenbart on 2006-06-16
I was also unable to do the live install from the live cd.  (Installing on a compaq 1200-xl118 laptop)  I could get as far as selecting a language and it would just lock up.

However, the alternate install cd worked better.  (I'm not completely up and running but at least the install completed successfully.)

---

### Post by xenblend on 2006-06-16
Yes the alternate cd worked for me too after many failures with the normal cd.

---

### Post by localzuk on 2006-06-16
I would definitely advise that you have a go with the alternative cd. I have not, as yet, managed to get the Desktop CD to work at all for installing...

---

### Post by starNIX on 2006-06-18
Confirmed...  The alternate install CD worked like a charm...  Expresso needs some work...

---

