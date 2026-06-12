---
title: "Advise for Ubuntu server: Redundancy / Imaging"
date: 2009-05-15
forum: General Help
---

### Post by ScottMartin on 2009-05-15
I would like to get some advise on managing a server for a small company.

I currently have a Ubuntu Server that is online and runs several websites as well as their email server.

Each night, the server is backed up using cron jobs/tar to a NAS drive as well as an external USB for offsite storage.

This is fine for maintaining the data itself, but I would like to be able to get a new server online as fast as possible and not have to worry about reinstalling everything manually.

Several thoughts:

Redundant server. How feasible is this ... Server 1 goes down, Server 2 ready to go online. What is needed if this is possible.

Create an exact mirror on the existing server so it can be restored to new hardware (what are the pitfalls of not having the exact same hardware on a Linux server)

Since the server is at a remote location, I would like to make this as painless as possible if the company needs to get back online ASAP.

Would apps such as PartImage,SystemRescueCD,Clonezilla be the best approach for creating an exact image for a fast restore?

Any suggestions would be appreciated on what the best approach would be.

Regards,
Scott.

---

### Post by dcstar on 2009-05-15
> **ScottMartin said:**
> I would like to get some advise on managing a server for a small company.

I currently have a Ubuntu Server that is online and runs several websites as well as their email server.

Each night, the server is backed up using cron jobs/tar to a NAS drive as well as an external USB for offsite storage.

This is fine for maintaining the data itself, but I would like to be able to get a new server online as fast as possible and not have to worry about reinstalling everything manually.

Several thoughts:

Redundant server. How feasible is this ... Server 1 goes down, Server 2 ready to go online. What is needed if this is possible.

Create an exact mirror on the existing server so it can be restored to new hardware (what are the pitfalls of not having the exact same hardware on a Linux server)

Since the server is at a remote location, I would like to make this as painless as possible if the company needs to get back online ASAP.

Would apps such as PartImage,SystemRescueCD,Clonezilla be the best approach for creating an exact image for a fast restore?

Any suggestions would be appreciated on what the best approach would be.

Regards,
Scott.

The dd command will copy your existing disk byte for byte, you can simply set a cron job up to do it whenever you like.

New server hardware should autodetect reasonably well, the main issue would be if a different network card was assigned a new designation that did not match what was in the old server.

---

