---
title: "Update Manager problem - Repos missing?"
date: 2011-02-17
forum: Desktop Environments
---

### Post by HeIsRisen on 2011-02-17
This is the error that the update manager kicks out. I am an running a pretty fresh install, hickup free until now using 10.10, Dual Boot with Win 7 (rarely used) and my internet connection is working flawlessly otherwise.

W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Krytarik on 2011-02-18
Just remove gdm2setup's PPA from the sources list:
"System -> Administration -> Software Sources -> Other Software"

Then re-add the PPA if you want:
[https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)
```

sudo add-apt-repository ppa:gdm2setup/gdm2setup
sudo apt-get update

```
Or via the "Software Sources" dialog.

---

### Post by HeIsRisen on 2011-02-18
Will try in the AM. Not at home, thanks.

---

### Post by HeIsRisen on 2011-02-19
Well, it solved my problem but when I tried to reinstall I got errors 404 on two of them

---

### Post by Krytarik on 2011-02-19
> **HeIsRisen said:**
> Well, it solved my problem but when I tried to reinstall I got errors 404 on two of them
Two? I thought it was only about gdm2setup?

However I it also in my repo list, since shortly after I installed Lucid in ocober last year, and never get an error. Weirdly, that you don't get errors on all the other repos as well, since I suspect a misconfiguration of your router/firewall or generally laggy internet access.

---

### Post by HeIsRisen on 2011-02-19
Well two instances of that reo on the other sources list. I have fios ....28 megs down and 15 megs up ... so not my inet. Why is it just now a problem with my router/firewall? These repos have been there since day one of my install

Running 10.10

---

### Post by Krytarik on 2011-02-19
Which are the two repos then you get errors for?

Do you have a router then, or configured a special firewall?

---

### Post by bapoumba on 2011-02-19
I get a 404 from the link you provided in the first post. Do you have the proper url ?

---

