---
title: "No title bat after installing Beryl"
date: 2008-02-16
forum: Desktop Effects &amp; Customization
---

### Post by nirfun1 on 2008-02-16
Hi all,
I'm new to linux and I've installed Ubuntu 7.10

I installed Beryl but I can't see title bars on all windows.

I tried several things from google and from this forum with no success.

any help?
Thanks.

---

### Post by aashay on 2008-02-16
find and install "emerald" from the repositories. In case it doesnt autostart, run "emerald --replace" from a terminal.

---

### Post by nirfun1 on 2008-02-16
I already have emerald installed.

 emerald --replace returns an empty line on terminal

---

### Post by luvinit on 2008-02-16
This can be a graphics driver problem, make sure it is installed correctly.

---

### Post by nirfun1 on 2008-02-16
> **luvinit said:**
> This can be a graphics driver problem, make sure it is installed correctly.

How can I make sure that the driver is installed correctly?

---

### Post by luvinit on 2008-02-17
Most people either go with restricted drivers manager in system>administration or use something called Envy.

---

### Post by chavanak on 2008-02-17
If you have an nvidia or ati driver, i recommend envy. It does the job perfectly including  configuring the xorg.conf file

---

### Post by FuturePilot on 2008-02-17
First Beryl is no longer being developed. Beryl was merged back into Compiz to become Compiz Fusion. 
Installing Emerald from the Ubuntu repos will not work because that version is specifically for Compiz Fusion.
Ubuntu 7.10 comes with Compiz Fusion already installed. If you already have your graphics driver installed try going System&#8594;Preferences&#8594;Appearance and click on the Visual Effects tab.

---

