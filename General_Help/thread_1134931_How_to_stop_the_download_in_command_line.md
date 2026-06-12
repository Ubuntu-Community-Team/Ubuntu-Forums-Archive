---
title: "How to stop the download in command line?"
date: 2009-04-24
forum: General Help
---

### Post by alcatraz678 on 2009-04-24
Guys,

I have downloaded something very huge size, it's still running now.. I want to stop it cause it will take days to complete the download..

I used the apt-get install..

Now if i closed the command line Im afraid that some files that have been downloaded will still be in my system..

Is there a way to formally stop the download and rollback the system?

---

### Post by iaculallad on 2009-04-24
While on the terminal, press Ctrl+C to abort the download/installation. Afterwards, try issuing the terminal commands below:

```
sudo apt-get autoclean && sudo apt-get autoremove
```

---

### Post by alcatraz678 on 2009-04-24
Hey,

I tried the Ctrl C and I can use the command line again.

Then the autoclean and autoremove didn't remove any files

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del acroread 9.1.0-7jaunty1 [63.4MB]
Del nvidia-common 0.2.10 [10.3kB]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So does that mean my system is clean?

---

### Post by jimv on 2009-04-24
Yep, you're fine.

---

### Post by iaculallad on 2009-04-24
> **alcatraz678 said:**
> Hey,

I tried the Ctrl C and I can use the command line again.

Then the autoclean and autoremove didn't remove any files

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del acroread 9.1.0-7jaunty1 [63.4MB]
Del nvidia-common 0.2.10 [10.3kB]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So does that mean my system is clean?

You're good. If you like you could delete the partial files downloaded during the process.

Files are stored at /var/cache/apt/archives/partial location.

---

