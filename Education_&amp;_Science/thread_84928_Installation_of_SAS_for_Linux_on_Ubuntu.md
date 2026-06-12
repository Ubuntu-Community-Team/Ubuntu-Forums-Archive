---
title: "Installation of SAS for Linux on Ubuntu?"
date: 2005-11-01
forum: Education &amp; Science
---

### Post by retiefdv on 2005-11-01
I am slightly uncertain where to post this question, but since this is about my personal use of Ubuntu as a desktop, I thought this area would be appropriate.

I am considering moving to Linux for all my dekstop needs. I have played around with various distro's and the time for my final decision is near. Ubuntu is obviously one of the prime candidates for my desktop.

There is however a proprietary application that I use a lot, namely SAS. SAS has a Linux version, but they specify on their web site that it can only be used on Red Hat Linux or SuSE Linux. Does this really mean that I cannot run SAS on Ubuntu at all?

---

### Post by hampus on 2005-11-01
Why don't you try to install it?

---

### Post by suRoot on 2005-11-01
It may or may not work, you'll only know after you try running it.

If they distribute it in RPM format, you can try installing it with alien:

```
sudo apt-get install alien

sudo alien "your_rpm_package_name".rpm

sudo dpkg -i "your_brand_new_deb_package_name".deb 
```

If they provide source, you can download & build from that.

If I were you, I'd build it & see what happens.

---

