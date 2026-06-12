---
title: "Trinity Desktop help"
date: 2012-02-22
forum: Desktop Environments
---

### Post by dagroves on 2012-02-22
I am trying to install the Trinity Desktop environment on Elementary OS Jupiter (Ubuntu 10.10)

I have done what is needed on this page for Ubuntu 10.10: [http://trinitydesktop.org/installation.php#ubuntu](http://trinitydesktop.org/installation.php#ubuntu)
I had no problems there, but when I do: 
```

sudo apt-get install kubuntu-default-settings-trinity kubuntu-desktop-trinity

```

I get this error in the terminal: [http://paste.ubuntu.com/853227/](http://paste.ubuntu.com/853227/)
Can someone help me out?
David

PS: Pay no attention to the blank code, for some reason it will not let me take that away... =-[

---

### Post by 3Miro on 2012-02-22
This is from your code:
```
The following packages will be REMOVED:
  foomatic-db-compressed-ppds **sudo**
```

You don't want to remove sudo from your system, I would wait for someone more knowledgeable to give an opinion, but I wouldn't try to install trinity until I hear it is safe to remove sudo.

As for the error, their server did not allow you to download libcaldav i386 0.6.5-2debian2. I don't know what the problem is, probably something to do with their server.

---

### Post by dagroves on 2012-02-22
> **3Miro said:**
> This is from your code:
```
The following packages will be REMOVED:
  foomatic-db-compressed-ppds **sudo**
```You don't want to remove sudo from your system, I would wait for someone more knowledgeable to give an opinion, but I wouldn't try to install trinity until I hear it is safe to remove sudo.

As for the error, their server did not allow you to download libcaldav i386 0.6.5-2debian2. I don't know what the problem is, probably something to do with their server.

Yeah I had caught that it was trying to remove sudo. Not sure why it wants to do that...

---

### Post by dagroves on 2012-02-24
***bump***

---

### Post by ohadcn on 2012-02-24
about the sudo:
don't worry, you remove sudo but install sudo-trinity & kdesudo-trinity which replace it

it look like a problem in the configuration of the repository you are trying to download from
```

 Err [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/) maverick/main libcaldav i386 0.6.5-2debian2
 403  Forbidden

```
this means that the server don't let you download the packages
i am not so expert in trinity but i think you need to change the server you are downloading from to another one (e,g:ftp.rezopole.net)
(open the package manager, look for software sources, choose different mirror and refresh packages lists)

---

### Post by Krytarik on 2012-02-24
> **ohadcn said:**
> it look like a problem in the configuration of the repository you are trying to download from
```

 Err [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/) maverick/main libcaldav i386 0.6.5-2debian2
 403  Forbidden

```this means that the server don't let you download the packages
Actually, I can visit that repo just fine, as well as download the actual package it's trying to fetch:
[QUOTE=dagroves]```
Failed to fetch [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/pool/main/libc/libcaldav/libcaldav_0.6.5-2debian2_i386.deb](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu/pool/main/libc/libcaldav/libcaldav_0.6.5-2debian2_i386.deb)  403  Forbidden
```[/QUOTE]So it must have been a temporary issue with the server of that repo back then (as the response status code "[403]("http://en.wikipedia.org/wiki/HTTP_403")" actually excludes issues on the client side, e.g. with firewall, proxy, etc.).

Regards.

---

### Post by dagroves on 2012-02-25
> **Krytarik said:**
> Actually, I can visit that repo just fine, as well as download the actual package it's trying to fetch:
So it must have been a temporary issue with the server of that repo back then (as the response status code "[403]("http://en.wikipedia.org/wiki/HTTP_403")" actually excludes issues on the client side, e.g. with firewall, proxy, etc.).

Regards.

So should I go there and just manually download the missing packages or what should I do?

---

### Post by Krytarik on 2012-02-25
> **dagroves said:**
> So should I go there and just manually download the missing packages or what should I do?
No, simply try it again, it should work now. The packages *ohadcn* has mentioned, "sudo-trinity" and "kdesudo-trinity", are in the list of to be installed packages; and in the worst case, you can always boot into recovery mode and reinstall "sudo" from the root shell prompt ("netroot"), which would obviously lead to the removal of some packages you are now about to install (incl. those mentioned above) and probably leave you with a broken DE; then you'd need to use "ppa-purge" to get rid of the Trinity PPA, remove all the left-over packages, and downgrade those it has upgraded. Good luck! :P

---

### Post by dagroves on 2012-02-26
> **Krytarik said:**
> No, simply try it again, it should work now. The packages *ohadcn* has mentioned, "sudo-trinity" and "kdesudo-trinity", are in the list of to be installed packages; and in the worst case, you can always boot into recovery mode and reinstall "sudo" from the root shell prompt ("netroot"), which would obviously lead to the removal of some packages you are now about to install (incl. those mentioned above) and probably leave you with a broken DE; then you'd need to use "ppa-purge" to get rid of the Trinity PPA, remove all the left-over packages, and downgrade those it has upgraded. Good luck! :P

Well that would be way to much trouble... nevermind then! Thanks for the help!

---

