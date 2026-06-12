---
title: "Error when updating, no public key found"
date: 2009-03-12
forum: General Help
---

### Post by AoA Linux on 2009-03-12
Hello, the notifier icon pops up saying I need to update my Ubuntu 8.10, but when it updates or I use the apt-get update in a terminal, it says error, no public key found...  I have used Ubuntu on many computers, but have never had this issue.  Any suggestions how to fix this? 

Thanks!

---

### Post by hockeyhead019 on 2009-03-12
the only time i get this is when i add a respository which needs a key... i really don't know how to fix it though... have you added anthing recently to the respository list?

---

### Post by AoA Linux on 2009-03-12
No sir, I have just installed ubuntu onto a computer and it said that the first time I tried to update it.

---

### Post by hockeyhead019 on 2009-03-12
that's weird... never heard of that before maybe just try a fresh install?

---

### Post by AoA Linux on 2009-03-12
I dono if this has anything to do with it because this is my first time using it but... it is Ubuntu Ultimate Edition?

---

### Post by sgosnell on 2009-03-12
It's not an error, just a warning.  Apt is warning you that it doesn't have a key for the repository, and can't verify it.  It will still get and install the apps if you tell it to.

If you're really worried about it, you can get the key with Firefox, and then have Synaptic install it, or you can open a terminal and input ```
sudo wget http://ftp-master.debian.org/ziyi_key_2006.asc -O - | sudo apt-key add -
```.

I usually just ignore it.

---

### Post by AoA Linux on 2009-03-12
Ok I see, I tried the command in the terminal and it said this  

HTTP request sent, awaiting response... 404 Not Found
2009-03-12 22:24:17 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

---

### Post by sgosnell on 2009-03-12
Sorry, I cut and pasted too quickly.  Replace the [http://ftp-master.debian.org/ziyi_key_2006.asc](http://ftp-master.debian.org/ziyi_key_2006.asc) with the URL of the key you want to get.

---

### Post by AoA Linux on 2009-03-12
Sorry for being a noob, but I don't really know what keys I need it brings up several errors saying keys are missing.

---

### Post by sgosnell on 2009-03-13
It should give you the keys in the error message, and you'll have to get each one individually.  Like I said, it's more trouble than it's worth.  Just ignore it, and go ahead and install the apps, as long as you're reasonably sure of the repository.  What you're getting is a warning from gpg, not a system error.

---

### Post by AoA Linux on 2009-03-13
Ok I see what your saying.  Thanks for the help!

---

