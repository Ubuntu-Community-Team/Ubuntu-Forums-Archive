---
title: "copy complete OS to DVD?"
date: 2012-11-29
forum: Desktop Environments
---

### Post by harlie on 2012-11-29
Can I copy the complete Ubuntu 12.04 OS including all current updates to a DVD?

I have the install disk but of course it has none of the updates so is not a very good backup. It seems possible to have the system wrecked some how and need a full backup of the OS. I have backups of the home folder so no problem there.

Harlie

---

### Post by robert shearer on 2012-11-29
Yes, using remastersys

[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

---

### Post by harlie on 2012-11-30
> **robert shearer said:**
> Yes, using remastersys

[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)


Thank you I will check it out.
Harlie

---

### Post by ugm6hr on 2012-11-30
Or you could just backup /var/cache/apt/archives
It is where all your debs are saved from update manager / synaptic / software centre etc.
Restoring just requires copying the files back to the same location and running an upgrade

---

### Post by harlie on 2012-12-01
> **ugm6hr said:**
> Or you could just backup /var/cache/apt/archives
It is where all your debs are saved from update manager / synaptic / software centre etc.
Restoring just requires copying the files back to the same location and running an upgrade


Thanks I will look at this too as a beginner I will look for the simplest one.

Harlie

---

### Post by robert shearer on 2012-12-01
The backup option of /var/cache/apt/archives
will allow you to reinstate all your **applications** and **updates** to a fresh install.

Remastersys does this **and** allows you to personalise the disc so your reinstallation has all the tweaks and desktop settings you may have modified from the standard install.

Why don't you try both as a learning experience..?
:)

---

### Post by harlie on 2012-12-07
> **robert shearer said:**
> The backup option of /var/cache/apt/archives
will allow you to reinstate all your **applications** and **updates** to a fresh install.

Remastersys does this **and** allows you to personalise the disc so your reinstallation has all the tweaks and desktop settings you may have modified from the standard install.

Why don't you try both as a learning experience..?
:)

I installed Remastersys and at the same setting installed Synaptic then my computer locked up and could do nothing at all I had to reinstall an earlier release and erase 12.04
so I had no luck I don't know which of the downloads caused the problem but I doubt it was synaptic. So now I am shy of Remastersys.

Harlie

---

