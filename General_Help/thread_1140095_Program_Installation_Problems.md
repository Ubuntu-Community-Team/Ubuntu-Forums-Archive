---
title: "Program Installation Problems"
date: 2009-04-27
forum: General Help
---

### Post by mitchrite on 2009-04-27
My windows is screwed, so I've switched to Ubuntu which I had as a backup

When I go to add new programs, such as BasKet, I get the following:

When I click "apply changes" after selecting a program, a window pops up saying 

"Warning
You are about to install software that can't be authenticated" etc etc "241 packages will be held back and no upgraded. 14 new packages will be installed"

and even if i click "apply" it tries to download the 14 packages but gives me this:

(I deleted some of the IP numbers)

"W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libksieve0_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libksieve0_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libmimelib1c2a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libmimelib1c2a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kaddressbook_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kaddressbook_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kresources_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kresources_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kio-plugins_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kio-plugins_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found[IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libk/libksba/libksba8_1.0.1-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libk/libksba/libksba8_1.0.1-2_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gpgsm_2.0.4-1ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gpgsm_2.0.4-1ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gnupg-agent_2.0.4-1ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gnupg-agent_2.0.4-1ubuntu3_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pinentry/pinentry-qt_0.7.3-1ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pinentry/pinentry-qt_0.7.3-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmail_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmail_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimexchange1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimexchange1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/korganizer_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/korganizer_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kontact_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kontact_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)
  404 Not Found [IP: 91.189.88]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/basket/basket_1.0.2-2build2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/basket/basket_1.0.2-2build2_i386.deb)
  404 Not Found [IP: 91.189.88]"


This has happened for a couple trusted programs now, and I have no idea what to do.

thanks

---

### Post by stucky on 2009-04-27
Looks like the IP is no good on the repository it's trying to hit. Or have you shortened it for some reason? Assuming that this machine can't actually reach the internet, you might try changing your software sources via System > Administration > Software Sources and see if that helps.

---

### Post by cariboo on 2009-04-27
I just did some Juanty update from the Canadian servers and had no problems. I would suggest you go to System-->Administration-->Software Sources and change to the main server.

---

### Post by mitchrite on 2009-04-27
So I did that, switched to "Main Server" but when I went to add programs it says the list is not available and needs to be refreshed.

It tries to download a bunch of new packages and gives this:

"http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.46 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.92.46 80]
"


I still don't know what that all means

:confused:

---

### Post by stucky on 2009-04-27
Is this on the machine you're posting from? If not, could you please verify that you do have a good network connection?

The server seems to be responding when I ping it just fine.

```

dave@gungnir:~$ ping -c3 91.189.92.46
PING 91.189.92.46 (91.189.92.46) 56(84) bytes of data.
64 bytes from 91.189.92.46: icmp_seq=1 ttl=52 time=189 ms
64 bytes from 91.189.92.46: icmp_seq=2 ttl=52 time=190 ms

```

---

