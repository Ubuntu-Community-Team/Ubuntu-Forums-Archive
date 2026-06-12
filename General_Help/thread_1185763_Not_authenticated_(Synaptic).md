---
title: "Not authenticated (Synaptic)"
date: 2009-06-12
forum: General Help
---

### Post by HavocXphere on 2009-06-12
On installing guake in synaptic I get a warning about stuff being unauthenticated.

[[Screenshot here]("http://rlhwzw.bay.livefilestore.com/y1pn8eY5XOQHqD2qKLdwVBm2iCmEVC4RRBVozIP1nEYiT6rHR9aNmZxgQFpUT6sO5T1cnKgmF62WDsGpftw4128wrRQRFGjdZ3q/Screenshot-Untitled%20Window.png")]

What exactly does this mean? Is the software not coming from the main servers? Or does it have something to do with the multiverse/universe distinction? Or something with signing?

I'd appreciate it if someone could help clarify.:D

---

### Post by michy99 on 2009-06-12
It is probably from a repository that you do not have the PGP key for. If you run```
sudo apt-get update
```it will show you which keys you do not have.

---

### Post by HavocXphere on 2009-06-12
Apologies for not responding immediately...I was busy fighting with a lock on apt & a mirror that appears to be down.

> Havoc@Xphere:~$ sudo apt-get update
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty Release.gpg
Get:1 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/main Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/main Translation-en_ZA
Get:2 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/restricted Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/restricted Translation-en_ZA
Get:3 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/universe Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/universe Translation-en_ZA
Get:4 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/multiverse Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/multiverse Translation-en_ZA
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates Release.gpg
Get:5 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/main Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/main Translation-en_ZA
Get:6 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/restricted Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/restricted Translation-en_ZA
Get:7 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/universe Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/universe Translation-en_ZA
Get:8 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/multiverse Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/multiverse Translation-en_ZA
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security Release.gpg
Get:9 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/main Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/main Translation-en_ZA
Get:10 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/restricted Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/restricted Translation-en_ZA
Get:11 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/universe Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/universe Translation-en_ZA
Get:12 [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/multiverse Translation-en_ZA
Ign [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/multiverse Translation-en_ZA
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty Release
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates Release
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security Release
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/main Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/restricted Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/universe Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty/multiverse Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/main Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/restricted Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/universe Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-updates/multiverse Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/main Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/restricted Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/universe Packages
Hit [ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za) jaunty-security/multiverse Packages
Reading package lists... Done
Havoc@Xphere:~$ 

Not sure what the business about Ign is about, but I don't see anything about keys.

After switching mirrors (From the ubuntu ZA -> mirror.ac.za), the app installed and I haven't seen the error again. Weird.:confused:

---

