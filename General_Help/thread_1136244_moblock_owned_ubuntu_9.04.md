---
title: "moblock owned ubuntu 9.04"
date: 2009-04-24
forum: General Help
---

### Post by donald7777 on 2009-04-24
Hello, I did a fresh install with ubuntu 9.04. I than installed moblock folling the sites instructions and used the 8.10 deb file. Moblock failed on install. now when i try to shutdown. it freezes at stopping moblock daemon. please help.
    I have tried through the terminal a purge and a remove but it always freezes at stopping daemon.

---

### Post by donald7777 on 2009-04-24
Also a side question. Is Vuze(azureaus) available for 9.04? i tried installing my old deb and says it cant fnd this old java file that has been marked obsolete.

---

### Post by lovinglinux on 2009-04-24
> **donald7777 said:**
> Hello, I did a fresh install with ubuntu 9.04. I than installed moblock folling the sites instructions and used the 8.10 deb file. Moblock failed on install. now when i try to shutdown. it freezes at stopping moblock daemon. please help.
    I have tried through the terminal a purge and a remove but it always freezes at stopping daemon.

Instead of using an old deb, use the repository for Jaunty. It works perfectly.

```
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
```

To get the key for this specific repository

```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```

The freezing p&#341;oblem is due to missing *iptables-custom-insert.sh* and *iptables-custom-remove.sh* in the /etc/blockcontrol/ folder.  Just copy those from an old installation and you will be fine. talz13 has uploaded both for those that do not have a copy. Get them [here](http://ubuntuforums.org/showpost.php?p=7138861&postcount=259). I don't know if he deleted his rules before uploading, so check the files content before using them.

---

### Post by donald7777 on 2009-04-24
> **lovinglinux said:**
> Instead of using an old deb, use the repository for Jaunty. It works perfectly.

```
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
```

To get the key for this specific repository

```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```

The freezing p&#341;oblem is due to missing *iptables-custom-insert.sh* and *iptables-custom-remove.sh* in the /etc/blockcontrol/ folder.  Just copy those from an old installation and you will be fine. talz13 has uploaded both for those that do not have a copy. Get them *here*. I don't know if he deleted his rules before uploading, so check the files content before using them.

2 things cant click on here because it is not an hyperlink
otherthing i get this error when trying to add the key
donald@ubuntu:~$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg: WARNING: unsafe ownership on configuration file `/home/donald/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

---

### Post by lovinglinux on 2009-04-25
> **donald7777 said:**
> 2 things cant click on here because it is not an hyperlink
otherthing i get this error when trying to add the key
donald@ubuntu:~$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv 9C0042C8
gpg: WARNING: unsafe ownership on configuration file `/home/donald/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

[Link](http://ubuntuforums.org/showpost.php?p=7138861&postcount=259) fixed. I don't know about the key. It worked for me, just added the repository, then downloaded the key.

---

### Post by jre on 2009-04-25
First of, my last version in jaunty was broken, sorry. 
I have **fixed it in blockcontrol_1.4.1-1~jaunty**. I'm just uploading the package, it should be available in a few minutes.
**During the update from the current broken jaunty package this one will hang again. So you have to interrupt (press "control" + "c") the update in order to force the use of a new script. Then everything will work.**

On updates from older, non-broken versions or on new installations everything will work flawless.

The problem was that the custom iptables scripts aren't installed to /etc/blockcontrol/ any more. Instead they go to /usr/share/doc/blockcontrol/examples and blockcontrol will execute every ...insert.sh or ...remove.sh script that is in /etc/blockcontrol/. This might be useful for a future mobloquer release, which might allow easy whitelisting of IP+port combinations.
Unfortunately my last version was broken if none such script existed.



About the key problem: First time I hear this. But just try another method to add my gpg key, follow the instructions here:
[https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa)
and follow that link [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by donald7777 on 2009-04-27
Ok, added your key following your instructions and it took. That is new. Oh well, Moblock is completely removed right now. checked the sources and your info if correct. so will try installing again with this command.
```
sudo aptitude install moblock blockcontrol mobloquer
```

---

