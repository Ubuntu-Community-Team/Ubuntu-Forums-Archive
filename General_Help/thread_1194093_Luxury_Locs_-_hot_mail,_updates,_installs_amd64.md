---
title: "Luxury Locs - hot mail, updates, installs amd64"
date: 2009-06-22
forum: General Help
---

### Post by LuxuryLocs on 2009-06-22
Hello All;
   I am new and am having three major issues, that i need help with.
A)i cant open letters in hot mail
B)i cant update repositories
C)i cant install packages, error cant install on your machine type amd64

---

### Post by Sef on 2009-06-24
> A)i cant open letters in hot mail

That is most likely Microsoft's doing because you are not using Windows.   I can open email, but cannot reply.


> B)i cant update repositories

Open the terminal (applications > accessories), then copy and paste in this command:

```
sudo apt-get update
```Copy and paste any errors that appear.


> C)i cant install packages, error cant install on your machine type amd64

If B works fine, then copy and paste this command in the terminal:

```
sudo apt-get upgrade
```Copy and paste any error messages that you get.

---

