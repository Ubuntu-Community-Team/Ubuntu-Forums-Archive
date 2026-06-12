---
title: "hwdata missing final newline"
date: 2006-09-06
forum: Desktop Environments
---

### Post by esjay on 2006-09-06
```

E: /var/cache/apt/archives/libssl0.9.8_0.9.8a-7ubuntu0.1_i386.deb: files list file for package `hwdata' is missing final newline

```

I get this error everytime I try to install, upgrade, remove anything. It seemed to happen spontaneously because the afore mentioned procedures worked fine for quite a while and I've never tampered with 'hwdata'. Ubuntu has crashed quite often recently if that's relevant. Can someone please help me decipher what this means because this error is driving me insane. ](*,) . Thanks :mrgreen:

---

### Post by hordur on 2006-10-19
Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.

---

