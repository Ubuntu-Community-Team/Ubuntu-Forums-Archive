---
title: "ClamAV - easy to understand user docs?"
date: 2009-02-20
forum: General Help
---

### Post by danbuter on 2009-02-20
I installed ClamAV via Synaptic. However, I can not figure out if it's running, etc. I type in clamav into terminal and get command not recognized. How am I supposed to actually run this? Thanks!

---

### Post by dcstar on 2009-02-20
> **danbuter said:**
> I installed ClamAV via Synaptic. However, I can not figure out if it's running, etc. I type in clamav into terminal and get command not recognized. How am I supposed to actually run this? Thanks!

You look in the properties of the clamav package and see what files have been installed, then you can run the appropriate command - or you install the **clamtk** GUI interface package.

---

### Post by binbash on 2009-02-21
I also suggest installing clamtk.It is a nice gui.However you have to stop apparmor (sudo /etc/init.d/apparmor stop) to upgrade the signatures (then you can start the apparmor)

---

### Post by hyper_ch on 2009-02-21
are you sure you even need ClamAV?

---

### Post by Malta paul on 2009-02-21
To use ClamAV in the terminal type in 'Clamscan' or 'Clamscan -r' for a full scan.

---

### Post by Malta paul on 2009-02-21
Bye the way if you need the latest ClamAV documents go to:
[http://www.clamav.net/doc/latest/](http://www.clamav.net/doc/latest/)
:D

---

### Post by danbuter on 2009-02-21
> **hyper_ch said:**
> are you sure you even need ClamAV?

Yes. I don't like forwarding viruses to my friends who don't use linux. ;)

I installed Clamtk and it's working great. Thanks, everyone!

---

### Post by hyper_ch on 2009-02-21
so you prefer to get them infected by strangers ;)

---

