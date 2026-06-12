---
title: "Quick VirtualBox Question"
date: 2009-04-11
forum: General Help
---

### Post by Universal344 on 2009-04-11
I am running VirtualBox 2.1.4 and when I started it last, it told me version 2.2.0 was available for download at virtualbox.org.  I was wondering if I can simply download and run the binary and it will see I have an old version and update it or do I have to uninstall the old version first and then install the new one.  If so, how do I do a clean uninstall?  Thank you for any help you can provide.

---

### Post by albinootje on 2009-04-11
> **Universal344 said:**
> I am running VirtualBox 2.1.4 and when I started it last, it told me version 2.2.0 was available for download at virtualbox.org.  I was wondering if I can simply download and run the binary and it will see I have an old version and update it or do I have to uninstall the old version first and then install the new one.  If so, how do I do a clean uninstall?  Thank you for any help you can provide.

Did you install it from the virtualbox.org website in the past, or via Synaptic Package Manager or apt-get (or add/remove) ?
If the first, you can add the virtualbox repositories from here, scroll down to this part:
> 
Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:

Then you probably have to remove the old package, and then install the  package virtualbox-2.2.
You can check the availability of the different virtualbox versions (2.0 vs. 2.1 for example) with :
```

apt-cache search virtualbox

```

---

### Post by binbash on 2009-04-11
If you installed previous one via deb package, just download the new deb and install.You don't have to remove old one.

---

### Post by Universal344 on 2009-04-11
I had originally installed v.2.1.4 with the .deb from their site.  However, when I run the new one it tells me there is a conflict with version 2.1.4 currently being installed and won't let me run the installer for 2.0.0.  How do I uninstall the old VBox.  Is it just gdebi uninstall VirtualBox?

---

### Post by albinootje on 2009-04-11
> **Universal344 said:**
> However, when I run the new one it tells me there is a conflict with version 2.1.4 currently being installed  

```

sudo apt-get remove --purge virtualbox-2.1
sudo apt-get install virtualbox-2.2 (or via Gdebi)

```

---

### Post by Universal344 on 2009-04-11
Thank you worked perfectly.

---

