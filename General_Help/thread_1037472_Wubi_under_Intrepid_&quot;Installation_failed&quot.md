---
title: "Wubi under Intrepid: &quot;Installation failed&quot; error"
date: 2009-01-11
forum: General Help
---

### Post by t-timmy on 2009-01-11
Hi.

This didn't appear in the FAQs, the stickies, or under a reasonable search.

After running Wubi under XP (which, for some reason, downloaded the whole ISO from the internet even though I ran it from a CD, but nevermind that...), I boot into the Ubuntu entry.

During the "Checking installation" progress bar I get a "Installation failed" message. The message indicates that there are logs under c:\ubuntu-installation-logs.zip or something similar.
I couldn't find that file after rebooting into XP.

Intrepid's a real disappointment so far, I've installed 8.04 using Wubi, and so far it seems fine.

If I can triple boot XP, 8.04 and Intrepid using Wubi I'll do that to provide more of the bug's information, just tell me what to do.

Cheers.

---

### Post by cybergrunt on 2009-01-14
I got this error because I was using a proxy and behind too many firewalls at the University where I work which tells me, at least for me, that it is port related.

---

### Post by HunterThomson on 2009-01-14
I have never used that wubi thing... still sounds like a bad idea to me. But if it lets you install wile 'not' connected to the internet then try that. I could not install Archlinux wile connected to the internet for some reson. So, I just installed offline no problem

---

### Post by t-timmy on 2009-01-14
The problem occurs after Wubi created its image, and then booting into the Ubuntu installation.
There couldn't be an internet connection, it's just the installation.
In any case, my wireless network is WPA encrypted, so even if the installation attempted to connect, it would fail.

I don't think this is the problem here...

---

### Post by azmo35 on 2009-01-14
Hi, i sugest you to delete everything wubi [8.10] on add and remove in windows, if you have the iso put the two on the same folder switch off your internet connection only to be sure that wubi not will get a new one and make a fresh install.):P

---

### Post by t-timmy on 2009-01-14
> **azmo35 said:**
> Hi, i sugest you to delete everything wubi [8.10] on add and remove in windows, if you have the iso put the two on the same folder switch off your internet connection only to be sure that wubi not will get a new one and make a fresh install.):P

Hi,

Thanks for trying to help.

I don't have the ISO, just a 8.10 CD.

I've uninstalled Wubi completely, running Wubi again through the CD with no internet connection.
Same issue. "Installation error", like I said in the first post.

---

### Post by azmo35 on 2009-01-15
Hi, again but are you sure that wubi is 8.10 and the iso on the cd is Intrepid 8.10 if so i'm without ideias.
[PHP]
Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.
[/PHP]

---

### Post by t-timmy on 2009-01-15
> **azmo35 said:**
> Hi, again but are you sure that wubi is 8.10 and the iso on the cd is Intrepid 8.10 if so i'm without ideias.
[PHP]
Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO. It is recommended to let Wubi download the ISO for you.
[/PHP]

Yes, CD is 8.10 downloaded and burnt.

---

### Post by azmo35 on 2009-01-15
And about wubi is 8.10 ?

---

### Post by t-timmy on 2009-01-15
> **azmo35 said:**
> And about wubi is 8.10 ?

I just pressed "Install inside Windows" when the screen came up.
It's the Wubi that was in the 8.10 CD.
So I guess that means yes, it is a 8.10 Wubi.

---

### Post by azmo35 on 2009-01-15
Sorry i forget that wubi was part off Ubuntu, have you tryed run wubi again or maybe you could downlod the wubi.exe from the web site.

---

