---
title: "GDM crashes every two days"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Sef on 2006-03-30
About every two days, GDM crashes and X org shutdown, so I have to reinstall Ubuntu.  

Why is it doing this?  What can I do?  What do I need to do?  Any help would be appreciated.  Thank you in advance.


system: itel P3 1.3 GB, 512 ram

---

### Post by Boyd on 2006-03-30
Maybe GDM, etc., is just dying, and needs restarting.  It would be unusual to have to reinstall, unless you have a bad disk.  If you open a terminal window, you can look at recent errors with the *dmesg | more *command.  The less recent errors are logged in /var/log/messages.0, and /var/log/syslog.0

HTH
Boyd

---

### Post by Sef on 2006-03-30
> unless you have a bad disk

By a bad disk, do you mean the hard drive?

---

### Post by Boyd on 2006-03-30
Sorry - I just now checked back on this thread.

Yes, I mean an error on the hard drive, or some other hardware error.  The system logs might show these, if that is what is happening.

Boyd

---

### Post by Sef on 2006-03-30
Like it is the hard drive as it is at least 5 years old, i believe.  This computer was put together piece by piece a while ago.  Just had the motherboard replaced a few months ago.

---

### Post by Jason_25 on 2006-03-30
Make sure you don't have memory errors that are corrupting your drive.  Memtest86 is on the install cd.

---

### Post by Sef on 2006-03-30
Thanks for the tip. Will do the memtest 86 tonight as i know it takes a while.

---

### Post by Sef on 2006-03-30
Also before it crashes, on boot up, I see this message:  'Mounting Local Systems - Failed.'

---

### Post by Sef on 2006-03-31
bump

---

