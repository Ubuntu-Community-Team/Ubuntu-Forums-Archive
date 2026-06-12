---
title: "Google Earth 5 crashes"
date: 2009-02-03
forum: General Help
---

### Post by void09 on 2009-02-03
When I run Google earth 5.0 on Ubuntu 8.10 I can see the GUI for a few seconds. Then it crashes.

Messages to shell:

user@Laptop:~/bin/google-earth$ ./googleearth
Warning: Unable to create prefs directory '/home/user/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

How do I fix this? Any ideas?
Thanks

---

### Post by wochti on 2009-02-03
[http://ubuntuforums.org/showthread.php?t=1059172&highlight=google+earth]("http://ubuntuforums.org/showthread.php?t=1059172&highlight=google+earth")

take a look at that

---

### Post by gjoellee on 2009-02-03
try this:
```

 cd /path/to/installation/folder
 mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```in my case the installation folder was in /home/$USER/google-earth (I did not install with sudo)

---

### Post by void09 on 2009-02-04
Thanks. That really helped :)

---

### Post by yogurtcz on 2009-02-07
> **gjoellee said:**
> try this:
```

 cd /path/to/installation/folder
 mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```in my case the installation folder was in /home/$USER/google-earth (I did not install with sudo)

Thx. works here too ;). Btw. if you installed from bin (using sudo) the default directory is:  

```

 cd /
 cd opt/google-earth
 mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```

---

### Post by DougieFresh4U on 2009-02-07
I downloaded the file and it installed itself wherever (I haven't looked) and then went to Applications>Internet, and it opened and ran with out a problem. Didn't have to fiddle around with any thing. :p

---

### Post by dstorrez on 2009-02-15
Thank you! that worked.

---

### Post by Paul Mitchell on 2009-02-15
> **gjoellee said:**
> try this:
```

 cd /path/to/installation/folder
 mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```in my case the installation folder was in /home/$USER/google-earth (I did not install with sudo)

Ditto. Works a treat here too.

---

### Post by shahidashrafi on 2009-03-06
Plz bare with me i am new to linux have ubuntu 8.04. I have the same problum with Google earth 5. I don't know how to do the code thing u have mentioned.

I would appreciate your step by step help:D

---

### Post by rudeboyskunk on 2009-03-08
This worked perfectly for me too!

shahidashrafi,

Just open up a terminal (Applications>Accessories>Terminal), type "cd googleearth" (without the quotes), and then copy and paste this line into the terminal:

mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

---

### Post by GOROSSI on 2009-03-29
Many thanks it works in Jaunty Jackalope beta

---

### Post by juliobahar on 2009-04-19
Thanks Dudes, 
This was a fast solution to my problem too.
Way to go Ubuntu

-My first post at Ubuntuforums -

---

### Post by linux_lover69 on 2009-04-27
Thank you, it worked wonders here to.

---

### Post by Gonzalo_VC on 2010-04-09
> **rudeboyskunk said:**
> This worked perfectly for me too!

shahidashrafi,

Just open up a terminal (Applications>Accessories>Terminal), type "cd googleearth" (without the quotes), and then copy and paste this line into the terminal:

mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

[COLOR="Navy"]Under Ub 8.04 64 bits with GoogleEarth 4.3 deleting that library did not solved the problem of crashing/restarting the session :(
It's **very** awful to see Linux crashing #-o[/COLOR]

---

