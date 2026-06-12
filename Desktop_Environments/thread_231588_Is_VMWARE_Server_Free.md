---
title: "Is VMWARE Server Free?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by nami on 2006-08-07
Hi,

I've been using VMWARE Server happely for a few weeks now and today I got the following message:

[[IMG]http://img158.imageshack.us/img158/9544/screenshotsp9.th.jpg[/IMG]](http://img158.imageshack.us/img158/9544/screenshotsp9.jpg)

Anyone know why I'm getting this message?

nami

---

### Post by deb2006 on 2006-08-07
You have to go to the VMWare site and get a license.
VMWare is "free" as in beer - but it's not free software (meaning OSS).

---

### Post by nami on 2006-08-07
how much is the licence?

---

### Post by iamhugeinjapan on 2006-08-07
The licence is free, you just have to give them contact information. Every couple of days they will send you a newsletter :\

---

### Post by nami on 2006-08-07
Do you have a direct link to the licences section, I can't seem to see it...

---

### Post by max_dingemans on 2006-08-07
I think [This]("http://register.vmware.com/content/registration.html") is what you're looking for.

---

### Post by nami on 2006-08-07
THanks

Ok, I have a serial number, where do I type it in?

---

### Post by iamhugeinjapan on 2006-08-07
Going from memory, I believe it's in the Help menu. There will be something about registering or entering a serial number or it's in the About VMWare bit.

---

### Post by nami on 2006-08-07
THanks found it.

But when I try to enter the serial number, it says I do not have permission, so I started vmware using "sudo vmware" and it allowed me to enter the password.  I closed vmware then tried opening it using the normal manor, and now it says:

> nami@nami-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/nami/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/nami/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-nami/ui-5610.log".  Please request support and include the contents of the log file.
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.


However, I can start it from the terminal using "sudo vmware", but how do I get the normal icon in the applications/systems tools menu to work again?

nami

---

### Post by Crashmaxx on 2006-08-07
Looks like you need to fix the permissions of "~/.vmware/preferences". Try this command:

```
sudo chmod 755 /home/nami/.vmware/preferences
```

---

### Post by sjbrun on 2006-08-07
Are you still running the beta version?
If so, this link may help:
[http://www.vmware.com/community/ann.jspa?annID=203]("http://www.vmware.com/community/ann.jspa?annID=203")

---

### Post by doogy2004 on 2006-11-09
does changing the permissions on that folder work?

---

### Post by stengah on 2006-11-17
Free as in "Free beer" as the saying goes ;-)

---

