---
title: "Update Manager wanting to update package"
date: 2009-03-06
forum: General Help
---

### Post by dashaund on 2009-03-06
Hey guys!  Long time searcher, first time thread starter.  I have a nagging issue that I can't seem to figure out:confused:.  I have a couple Macs on my home network and I'm using my Intrepid box as a file server and I'm running Netatalk and Avahi to allow my Macs to easily see my box.  I followed a couple guides online on how to install everything and set it up...everything is working great.  Part of the process was compiling Netatalk.  Well, after I compiled it, Update Manager sensed that there was an "update" for Netatalk (keep in mind I downloaded the source from the repositories).  Well, if I install the update it breaks Netatalk.  I went back and reinstalled Netatalk from my source and it worked again.  They're the exact same version, so I"m not sure why Update Manager wants to update.  I'm not really worried about it breaking anything, I'm happy the way it is, I just wanted Update Manager to stop alerting me that there's an update.  I've tried going in Synaptec and "locking" the version but it still doesn't stop alerting me.  I'm sure this is an easy fix, I just can't seem to figure it and haven't been able to find a relevant post on anything like this.  Thanks for the help!  The support I find here is definitely the best I've ever experienced.  If it's broken, there's always a solution to be found here, so thanks very much for the help and keep it up!

---

### Post by Giant Speck on 2009-03-06
Try finding the package in Synaptic.  Once you find it, click on it and go to Package -> Lock Version.

---

### Post by dashaund on 2009-03-06
> **Giant Speck said:**
> Try finding the package in Synaptic.  Once you find it, click on it and go to Package -> Lock Version.

I tried this.  In Synaptic it shows "netatalk" in red and it says it's locked, however, it's still prompting me for an update.

---

### Post by jzimmerman on 2009-03-16
Try the following from a terminal window...

```

echo "netatalk hold" | sudo dpkg --set-selections

```

I don't use the gui on my netatalk server, but it seems to work for me with aptitude update/upgrade from the console.

---

### Post by dashaund on 2009-03-17
> **jzimmerman said:**
> Try the following from a terminal window...

```

echo "netatalk hold" | sudo dpkg --set-selections

```

I don't use the gui on my netatalk server, but it seems to work for me with aptitude update/upgrade from the console.

AWESOME! That worked!  Thank you, thank you, thank you!

---

