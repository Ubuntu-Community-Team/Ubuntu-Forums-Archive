---
title: "How to find a third party repository address?"
date: 2010-12-13
forum: Desktop Environments
---

### Post by nrundy on 2010-12-13
I'm new to Ubuntu. I wanted to add Avast Anti-Virus. My understanding is that a good method is to add a third party repository. In general, how does one find third party repository addresses? Does one just do a Google search (e.g., Avast AntiVirus repository)? This didn't seem to produce the result I was looking for when I tried it. Should I go to the third party's website and search it out there? Are most third party repositories listed somewhere within the Ubuntu world?  Is there an efficient way to go about locating the legit address of a third party repository? After reading up on Linux and viruses I may not install Avast afterall, but I'm still interested in how I would go about finding a third party repository address. Thanks so much for your help guys.

---

### Post by Frogs Hair on 2010-12-13
Avast comes as a.deb package , so you simply download it and install it with the gdebi package installer and the source will be added to your list , unlike a ppa which requires a source list prior to installation. Sources  and packages for ppas can be found at Launchpad .net .

---

### Post by Krytarik on 2010-12-13
Nowadays many third party developers make their packages available via ppas AND deb-packages. If available I would always chose to install them via ppa, because they will be updated automatically if a new version becomes available. Like Frogs Hair's post implicates, Avast makes their packages ONLY available via direct download of the deb-packages, unfortunately. Personally a search for ppas via Google.

---

### Post by Alan James on 2010-12-13
I always find third-part applications by searching for them on Google. I have also looked on Launchpad.net, which can kinda be thought of as Canonical's “App Store.” It's a site where developers can upload their program and source code and have it be easily added to Ubuntu's repositories.

Also, I wouldn't install a virus protection software. Linux really doesn't need one. It's pretty bullet proof.

---

### Post by Krytarik on 2010-12-13
> **Alan James said:**
> I always find third-part applications by searching for them on Google. I have also looked on Launchpad.net, which can kinda be thought of as Canonical's “App Store.” It's a site where developers can upload their program and source code and have it be easily added to Ubuntu's repositories.

Also, I wouldn't install a virus protection software. Linux really doesn't need one. It's pretty bullet proof.
You are probably right. But I'm also using Avast on a on-demand basis to check files intended for use in Windows.
But that's not the topic.;)

---

### Post by nrundy on 2010-12-15
> **Alan James said:**
>  
Also, I wouldn't install a virus protection software. Linux really doesn't need one. It's pretty bullet proof.

I'm brand new to Ubuntu so I appreciate all you guy's help. The other day I was browsing the web with Windows and went to the ZenCast website where you can get a program to download Podcasts. Avast alerted that a Trojan was embedded in one of the advertisements on the webpage I was on. Avast stopped the auto-download (thankfully).   To make sure I am 100% informed: I do NOT have to worry about this sort of infection if I was browsing with Ubuntu and went to that same page that had the advertisement infection? I'm very nervous to not have protection cause I've used Windows forever. Simply put, Ubuntu cannot be infected by that Trojan that was in the advertisement? I can browse the web without a &quot;virus scanner&quot; running via a proxy and be perfectly safe?   :) Being a longtime Windows user I'm finding this hard to believe :)

---

### Post by Krytarik on 2010-12-15
Cause obviously nobody else wants to give an answer on the security matter:

[http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed](http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed)

I'm really sensitive to security, and for Windows I'm instantly advising, even begging;), to install a personal firewall and virus-protection. But Linux is completely different case, not only has it different commands and structure, which is why viruses written for Windows cannot bite it, even if it where completely open for access, one has to write viruses specificly for Linux, which is even until now only used by circa 1% of the computer users, sadly (for the others;)). Also the way it handles permissions is much, much deeper rooted than in Windows, which until Vista doesn't had any effective at all.

So, is it completely impossible to get a Linux system infected? No.
But even without a virus-protection it is much more safer then the best protected Windows sytem. I would say it stands at 99%.

---

