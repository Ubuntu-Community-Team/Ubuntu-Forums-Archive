---
title: "Valve Steam installation problem"
date: 2013-05-16
forum: Gaming &amp; Leisure
---

### Post by Locus Kiesselbachi on 2013-05-16
Hello!

Downloaded package from valve steam homepage. During installation it gives me this error:
```
Failed to fetch http://**ee**.archive.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.27.0-1ubuntu1.1_amd64.deb 404  Not Found [IP: 91.189.91.15 80]
```
I think it tries to download something from local Ubuntu server (**ee** as Estonia), but cant. 

What to do?
How can I change server?
Any other toughts

Lubuntu 12.10

---

### Post by CatKiller on 2013-05-16
It's been a while since I've used LXDE, but you can fiddle with the repository servers in Synaptic.

You might need to just refresh your local index (sudo apt-get update) though: I've occasionally got a 404 when trying to download a package that has been updated on the server since the last time I downloaded the package list.

---

### Post by Locus Kiesselbachi on 2013-05-16
```
sudo apt-get update
```

wow - it made progress, it is now updateing steam.

Thank you!

---

