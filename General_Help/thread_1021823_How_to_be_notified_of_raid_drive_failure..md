---
title: "How to be notified of raid drive failure."
date: 2008-12-26
forum: General Help
---

### Post by CA_paul on 2008-12-26
I successfully setup a mirror raid device using mdadm and the mdadm.conf file. But is there a way to receive an email if a drive fails? I could do this in Fedora by adding 'raid-alert: user_name' to /etc/aliases.

Any help is appreciated.

---

### Post by dcstar on 2008-12-26
> **CA_paul said:**
> I successfully setup a mirror raid device using mdadm and the mdadm.conf file. But is there a way to receive an email if a drive fails? I could do this in Fedora by adding 'raid-alert: user_name' to /etc/aliases.

Any help is appreciated.

See if you can set up logcheck or log2mail to alert you.

---

### Post by linux_paul on 2009-01-11
> **CA_paul said:**
> I successfully setup a mirror raid device using mdadm and the mdadm.conf file. But is there a way to receive an email if a drive fails? I could do this in Fedora by adding 'raid-alert: user_name' to /etc/aliases.

Any help is appreciated.

Try installing a mail transport agent (I used exim4) and add the raid-alert line to /etc/aliases. Then in System > Administration > Services check the box for RAID disks management (mdamd).

Test it with the mdadm --fail command and you should get an email.

---

### Post by scolbeck on 2009-01-11
mdadm running in monitor mode will email you with any problems.  To setup mdadm to run in monitor mode as well as specify your email address, perform the following and answer the relevant questions:

```
sudo dpkg-reconfigure mdadm
```

If you want the email sent to an external email account, you must also setup something like exim4.

---

