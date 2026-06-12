---
title: "Install of Google Earth"
date: 2009-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arvadawest on 2009-02-24
Good day,

I just downloaded the latest version of Google Earth (goodearthlinux.bin).  How do I install it.  Newbie again, so line commands are not my strength.  Certainly not like just clicking on it and simply installing it.  Thank you for your help. :)

---

### Post by whoop on 2009-02-24
[http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/](http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/)
[http://ubuntuforums.org/showthread.php?t=1065536](http://ubuntuforums.org/showthread.php?t=1065536)

---

### Post by arvadawest on 2009-02-24
> **whoop said:**
> [http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/](http://www.econowics.com/linux/312/install-google-earth-50-in-ubuntu-linux/)
[http://ubuntuforums.org/showthread.php?t=1065536](http://ubuntuforums.org/showthread.php?t=1065536)

I went to the first site and followed the instructions.  I am curious when installing why did I have to typed ./(filename).  Why the ./ part?  I'm just learning ubuntu.  Thank you.  -aw

---

### Post by bapoumba on 2009-02-25
Moved to General Help.

---

### Post by binbash on 2009-02-25
This is how i got it working : 

[http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html](http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html)

---

### Post by arvadawest on 2009-02-25
> **arvadawest said:**
> I went to the first site and followed the instructions.  I am curious when installing why did I have to typed ./(filename).  Why the ./ part?  I'm just learning ubuntu.  Thank you.  -aw

Thank you.  I was able to get mine working.  I just followed the instructions and did a chmod ugo+rwx on the .bin file and typed in the ./filename and it worked.  Just do not know why I had to type the ./  but it worked.

Not sure why this was moved to general help

---

### Post by bapoumba on 2009-02-25
Sorry, it was not obvious from the thread you were using a Dell :)
Moved back.

---

### Post by arvadawest on 2009-02-25
> **bapoumba said:**
> Sorry, it was not obvious from the thread you were using a Dell :)
Moved back.

That is ok.  Thank you.  I just asked another of the Ubuntu staff wondering if posting to the general area would get more exposure.  Thank you :)  -aw

---

### Post by binary10 on 2009-02-25
> **binbash said:**
> This is how i got it working : 

[http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html](http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html)

The only thing I did different was to mv the crypto library, it didn't work strictly to the instructions.

cd /home/<user>/google-earth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup

---

### Post by arvadawest on 2009-02-25
> **binary10 said:**
> The only thing I did different was to mv the crypto library, it didn't work strictly to the instructions.

cd /home/<user>/google-earth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup

Good point.  Since I'm a newbie I didn't know why I had to type ./(filename).  Does the ./ refer to the parent directory, but it did work and installed.

I find learning Linux very difficult for some reason.  My ignorance is overwhelming, but I am trying.

---

### Post by TimDaniels on 2009-02-28
> **arvadawest said:**
> [...] Since I'm a newbie I didn't know why I had to type ./(filename).  Does the ./ refer to the parent directory, but it did work and installed....

You don't have to type "./" .  It merely means "within this directory", and it is implied for filename arguments in Unix/Linux/Solaris shells and probably other "*ix" OS shells.

*TimDaniels*

---

### Post by arvadawest on 2009-03-01
> **TimDaniels said:**
> You don't have to type "./" .  It merely means "within this directory", and it is implied for filename arguments in Unix/Linux/Solaris shells and probably other "*ix" OS shells.

*TimDaniels*

Ok.  So all I needed to do was just type in the filename while in that directory?  Thanks.

---

