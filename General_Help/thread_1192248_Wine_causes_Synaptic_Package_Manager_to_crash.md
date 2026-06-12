---
title: "Wine causes Synaptic Package Manager to crash ?"
date: 2009-06-19
forum: General Help
---

### Post by robrom78 on 2009-06-19
Howdy! I'm having an issue with Wine, in that it appears to be causeing Synaptic Package Manager to crash.  By crash, I mean that SPM will not even finish loading before I'm given the following error:

E: Type '--2009-06-19' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.


Any suggestions are greatly appreciated!  Thanks very much in advance!

---

### Post by michy99 on 2009-06-19
Run these commands in a terminal:```
sudo rm /etc/apt/sources.list.d/winehq.list
sudo apt-get update
```

---

### Post by robrom78 on 2009-06-19
That was successful, thanks!  When the update was done, it spit out this:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

---

### Post by raymondh on 2009-06-19
try (in terminal)

```
gpg --keyserver subkeys.pgp.net --recv 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
sudo apt-get update
```

---

### Post by robrom78 on 2009-06-20
> **raymondhenson said:**
> try (in terminal)

```
gpg --keyserver subkeys.pgp.net --recv 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
sudo apt-get update
```


Thanks Ray, it works right as rain now!  I'm still learning linux (tired of windows), and im working on my linux+ cert (part cause of work), but correct me if i'm wrong...  The first line of code added the key, the second line was a security measure, and the last was just an update string?  

Thanks again! :D

---

### Post by raymondh on 2009-06-20
> **robrom78 said:**
> Thanks Ray, it works right as rain now!  I'm still learning linux (tired of windows), and im working on my linux+ cert (part cause of work), but correct me if i'm wrong...  The first line of code added the key, the second line was a security measure, and the last was just an update string?  

Thanks again! :D

You are most welcome and congratulations :)
 
My knowledge of linux/ubuntu is very limited so pls. verify.......The first line was to source the key from a server ... the second line is the security measure and to add the key ... and the 3rd is your update string involving the key.

Good luck on your certification and happy ubuntu-ing.

---

