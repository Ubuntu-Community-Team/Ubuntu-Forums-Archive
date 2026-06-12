---
title: "Jaunty update, how?"
date: 2009-04-17
forum: General Help
---

### Post by Naz_Farooq on 2009-04-17
Hi guys,
I just want to know that how would I upgrade my ubuntu 8.10 interpid to ubuntu jaunty 9.04? Should I format previous ubuntu 8.10 1st or is it possible to upgrade it direct from internet?
Can any one let me know in details please. I would be appreciative.

---

### Post by P4oL1n0 on 2009-04-17
When ubuntu 9.04 will be released you can update your intrepid box via internet using the update-manager! It will ask if you want to upgrade intrepid to jaunty.

---

### Post by kpkeerthi on 2009-04-17
> **Naz_Farooq said:**
> Hi guys,
I just want to know that how would I upgrade my ubuntu 8.10 interpid to ubuntu jaunty 9.04? Should I format previous ubuntu 8.10 1st or is it possible to upgrade it direct from internet?
Can any one let me know in details please. I would be appreciative.

[http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10](http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10)

---

### Post by NikoC on 2009-04-17
A couple of weeks ago when running intrepid I updated to Jaunty alpha 6 via:
ALT + F2
update-manager -d

Worked for me...

---

### Post by P4oL1n0 on 2009-04-17
More info at [http://help.ubuntu.com/community/JauntyUpgrades]("http://help.ubuntu.com/community/JauntyUpgrades")

---

### Post by Naz_Farooq on 2009-04-17
> **NikoC said:**
> A couple of weeks ago when running intrepid I updated to Jaunty alpha 6 via:
ALT + F2
update-manager -d

Worked for me...

Thanks, it is started now but it gave me a message that AMD video driver is not available with the new version and it asked me to continue, I clicked yes. Would my Video driver not be working with jaunty 9.10?

---

### Post by Naz_Farooq on 2009-04-17
> **NikoC said:**
> A couple of weeks ago when running intrepid I updated to Jaunty alpha 6 via:
ALT + F2
update-manager -d

Worked for me...

It says 'You don't have enough disk space for new upgrade'
What should I do now, is it possible to upgrade in my ubuntu 16GB hard drive without formatting it. I have 3 partitions: (C:) 20GB for WindowsXP - (D:) 40GB fat32 for both WIN OS & Linux OS - (Z:) 17GB for Linux Ubuntu 8.10 & remaining 3GB as a shared memory.
Is it possible to upgrade it in the same 17GB Z:/ drive.

---

### Post by NikoC on 2009-04-21
Well it's been a while since I played aorund with partioning, but I think you can boot with the Ubuntu LiveCD, start gparted and resize your partitions from there!

---

