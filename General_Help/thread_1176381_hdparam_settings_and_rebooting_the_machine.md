---
title: "hdparam settings and rebooting the machine"
date: 2009-06-02
forum: General Help
---

### Post by Harry Muscle on 2009-06-02
Just a quick question about using hdparam to set the timeout for the hard drive to spin down and go to sleep.  Do I have to run the command after every reboot or do you just run it once and it's permanently written to the hard drive and is persistent between reboots?

Thanks,
Harry

---

### Post by dcstar on 2009-06-03
> **Harry Muscle said:**
> Just a quick question about using hdparam to set the timeout for the hard drive to spin down and go to sleep.  Do I have to run the command after every reboot or do you just run it once and it's permanently written to the hard drive and is persistent between reboots?

Thanks,
Harry

Make the changes in /etc/hdparm.conf

---

