---
title: "upgrade fails"
date: 2005-10-15
forum: Desktop Environments
---

### Post by dgermann on 2005-10-15
Hi--

I suspect this is a sources.list problem, but am not sure. Can anybody help decipher these error messages, please?

```
E: /cdrom//pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb:  subprocess dpkg-split returned error exit status 2
E: /cdrom//pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu12_i386.deb:  subprocess dpkg-split returned error exit status 2
E: /cdrom//pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb:  subprocess dpkg-split returned error exit status 2
E: /cdrom//pool/main/g/glibc/libc6_2.3.5-1ubuntu12_i386.deb:  subprocess dpkg-split returned error exit status 2

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

My sources.list is from ubuntu-guide.

Thanks!

---

### Post by katiad on 2005-10-16
I got the same errors.

---

### Post by phibxr on 2005-10-16
Hoary-backports in Breezy?

---

### Post by manicka on 2005-10-16
You need to comment out the references to the cdrom in your sources.list and comment out hoary backports. Then change all instances of hoary to breezy and you should then be able to upgrade.

That is if I'm assuming correctly that you are trying to do a dist-upgrade to breezy.

---

### Post by dgermann on 2005-10-16
manicka--

Eureka! You've solved it!

Thanks so much manicka.

Now, do I hae to make any changes to my sources.list after I am done? Uncomment the cdrom, for instance?

Thanks!

---

### Post by manicka on 2005-10-16
The hoary cdrom won't be much use to you, I'd uncomment it if it's still there.

---

### Post by dgermann on 2005-10-17
om--

Thanks!

Actually, I have the Breezy 5.10 CD: shoulld that now be uncommented?

Thanks for your to the point help, manicka.

---

### Post by manicka on 2005-10-17
It's up to you. Personally It drives me nuts being asked for the cd all the time so I comment it out. If you are on broadband it's a good option but I'd leave the cd there for dial-up.

---

### Post by dgermann on 2005-10-17
Thanks, OM, that's something new I just picked up from you!

You are good to "talk" with!

---

### Post by manicka on 2005-10-18
I used to have the Tibetan symbol for OM that is in the tibetan font as my signature but it looked too much like an image so I had to remove it. I just replaced it with the word om until I can think of something better for my sig.

cheers
Grant

---

### Post by dgermann on 2005-10-18
Grant--

Ooops! Sorry for that. I took manicka to be your last name, and the O for your first initial.

Isn't the om character kind of like a backwards 3?

Any way, thanks for all your help, Grant. :KS

---

