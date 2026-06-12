---
title: "Amarok 1.3.7 Packages released"
date: 2005-12-07
forum: General Help
---

### Post by GoldBuggie on 2005-12-07
Unless you missed it Amarok 1.3.7 had been released for kubuntu:cool:

[http://kubuntu.org/announcements/amarok-1.3.7.php](http://kubuntu.org/announcements/amarok-1.3.7.php)

---

### Post by 23meg on 2005-12-08
Will these work in Ubuntu? Anyone tried?

---

### Post by INMCM on 2005-12-08
Works fine and dandy for me.  I already had Amarok installed and all it installed were updated amarok and amarok-gstreamer packages.

---

### Post by 23meg on 2005-12-08
I couldn't resist and tried, and yes they do.

---

### Post by Rochvellon on 2005-12-08
[quote=GoldBuggie]Unless you missed it Amarok 1.3.7 had been released for kubuntu:cool:[/quote] Noob question: How do I download the new version? Through Adept?

---

### Post by 23meg on 2005-12-08
Add the repository line given in the link above to yout /etc/apt/sources.list file and then install with Adept, Synaptic or apt.

---

### Post by OMGsplosion on 2005-12-23
[QUOTE=23meg]Add the repository line given in the link above to yout /etc/apt/sources.list file and then install with Adept, Synaptic or apt.[/QUOTE]

I did that and then I opened the Synaptic Package Manager and it comes up with this error :( 

**W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-1.3.7_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)**

Any ideas please?

---

### Post by Totzo on 2005-12-23
I had to compile libtunepimp from source to get mp3 lookup tagging to work but apart from that it's all good

---

### Post by supenguin on 2005-12-23
No problems here. I've had better luck adding additional repositories by editing the sources.list file than through any of the package managers.  Smooth upgrade, no problems.

---

### Post by Rackerz on 2005-12-23
[QUOTE=OMGsplosion]I did that and then I opened the Synaptic Package Manager and it comes up with this error :( 

**W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-1.3.7_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)**

Any ideas please?[/QUOTE]

That error doesn't really mean much, nothing to worry about.

---

### Post by fordfan753 on 2005-12-23
Yeah, just reload your sources.

Anyone wanting lyrics support should use the SVN version of amaroK, because they've fixed the lyrics thing in there and the fix wont be out until the next release.

---

