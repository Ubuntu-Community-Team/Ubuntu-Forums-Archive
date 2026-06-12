---
title: "antivirus"
date: 2009-04-15
forum: General Help
---

### Post by i.arnav on 2009-04-15
i m using ubuntu 8.10

i installed clamav daemon antivirus through package manager

bt it doesnt shows any icon of installation

please help me how to scan my computer through that antivirus

---

### Post by sedawk on 2009-04-15
On the command line the scanner is called clamscan.

If you are looking for a graphical interface you might
have to install something additional like clamtk.

---

### Post by elliotn on 2009-04-15
I havent thought of AVs and havent been thinking of one except on my Xp

---

### Post by paradigm2 on 2009-04-15
> **elliotn said:**
> I havent thought of AVs and havent been thinking of one except on my Xp

On Linux it really isn't need so much at this point but if you have windows computers which are connected to it or do things such as send attachments to windows users then you might consider it mainly for the protection of the windows machines (infected files downloaded on ubuntu can still be transferred to windows computers which would be susceptible even though ubuntu might not be).

---

### Post by chriskin on 2009-04-15
a good option is bitdefender as well. clam never found any virus, bitdefender found a virus and a spyware. 

you can find it on their site (if you do not care about non free software at least - non free as in restricted use, closed source etc, not that you have to pay) with a free license

> **paradigm2 said:**
> On Linux it really isn't need so much at this point but if you have windows computers which are connected to it or do things such as send attachments to windows users then you might consider it mainly for the protection of the windows machines (infected files downloaded on ubuntu can still be transferred to windows computers which would be susceptible even though ubuntu might not be).


remind me why i should care about the others . heheh no , what you wrote is totally right

---

### Post by i.arnav on 2009-04-15
thanx

---

### Post by redbook4574 on 2009-04-15
> **chriskin said:**
> a good option is bitdefender as well. clam never found any virus, bitdefender found a virus and a spyware. 

you can find it on their site (if you do not care about non free software at least - non free as in restricted use, closed source etc, not that you have to pay) with a free license




remind me why i should care about the others . heheh no , what you wrote is totally right

Another worth considering is avg from grisoft it is essentially the same as the free version used by windows.

---

### Post by mb_webguy on 2009-04-15
The Linux version of AVG Free is a scanner only, and has no ability to quarantine or remove infected files.  ClamAV can.

And yes, ClamAV itself is a collection of command-line tools.  To get a GUI interface you'll have to install something like the clamtk or klamav packages.  You can also integrate ClamAV into Nautilus with the nautilus-clamscan package, which adds a "Scan for viruses" option in the right-click menu.

---

