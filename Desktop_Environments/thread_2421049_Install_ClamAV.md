---
title: "Install ClamAV"
date: 2019-06-15
forum: Desktop Environments
---

### Post by larry90 on 2019-06-15
Hello everyone,
I Just finished installing ClamAV from source (using their guide) but while i was testing it I noticed that there isn't any freshclam.log folder and that means i have no idea if clamav will automatically update the signatures or not...

I tried to change the freshclam.conf by removing  # in #UpdateLogFile /var/log/freshclam.log... but then sudo freshclam stopped working and got this: ERROR: Can't open /var/log/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/freshclam.log).

Sudo freshclam seems to be working if i let the #UpdateLogFile, but than I will have to update manually the antivirus... Can anybody help me?

Not sure if this can help, but freshclam is in local.
 whereis freshclam
freshclam: /usr/local/bin/freshclam /usr/local/etc/freshclam.conf


Thanks in advance, have a great day

---

### Post by Autodave on 2019-06-15
I believe that that program is no longer being updated: not sure though.  My question to you would be, "Why are you running a virus scanner on Linux?"  There is no need for one.  The only viruses that Clam detected (when it was working) were Windows viruses to prevent you from passing them along to you Windows' friends.  13 machines running here: 2 of them have very public accessibility.  No AV programs on any of them, not a single virus in 9+ years.

---

### Post by larry90 on 2019-06-15
I installed antivirus because I m dual booting windows and ubuntu and i often share files, documents, etc, I also pass them to some other ppl using windows. I tought ClamAV was a light and updated antivirus and that's why I installed it... maybe u have some suggestion?

---

### Post by coffeecat on 2019-06-15
> **Autodave said:**
> I believe that that program is no longer being updated: 

Why would you believe that?

@larry90, why are you compiling from source? Clamav is in the repositories and can be installed from whichever package manager you prefer. Updates to the virus signatures still appear to be being issued so reports of Clamav's demise might possibly be an exaggeration (with apologies to Mark Twain).

---

### Post by larry90 on 2019-06-15
I installed from source because the ClamAV version in ubuntu 18.04 is still 100.3 but in their site i found the version 101. Maybe i could simply remove my 101 version and install the one coming with ubuntu, even if the version is older, the virus database should be the same but i would fix my freshclam auto update problem.

Btw thank for your relpy

---

### Post by TheFu on 2019-06-15
> **Autodave said:**
> I believe that that program is no longer being updated: not sure though.  My question to you would be, "Why are you running a virus scanner on Linux?"  There is no need for one.  The only viruses that Clam detected (when it was working) were Windows viruses to prevent you from passing them along to you Windows' friends.  13 machines running here: 2 of them have very public accessibility.  No AV programs on any of them, not a single virus in 9+ years.

 E&O insurance mandates that AV be installed and running.  If I worked with Windows and had a file server, I'd consider running AV on that machine.  Same for an email server - where I do run AV. People still try to email viruses.

---

### Post by larry90 on 2019-06-15
Ok than here is the question :D
Better clamAV version 100.3 autoupdating or version 101.1 but with manual update?

Ty in advance for your opinion!

---

### Post by deadflowr on 2019-06-15
Use the version from the repos.
It'll give a warning of it being outdated, but always work as expected. (Or should)
The Ubuntu devs patch it regularly to keep it functional.
It gets security fixes which will come to you through regular system updates.
If you Install it manually from source you'd have to keep patching or reinstalling it yourself for every new fix that comes along.
So more convenient to just use the repo one.

---

### Post by Rubi1200 on 2019-06-15
> **deadflowr said:**
> Use the version from the repos.
It'll give a warning of it being outdated, but always work as expected. (Or should)
The Ubuntu devs patch it regularly to keep it functional.
It gets security fixes which will come to you through regular system updates.
If you Install it manually from source you'd have to keep patching or reinstalling it yourself for every new fix that comes along.
So more convenient to just use the repo one.

+1 could not have said it better.

---

### Post by larry90 on 2019-06-16
Ok than, as you all suggested I m going to install it from repos!
Thanks everyone for your help!
Have a good day!

---

### Post by cybrsaylr on 2019-06-16
Curious on how many run an AV program on Linux?

Ask this because I've been using Linux, mainly Ubuntu since 2007 with no AV and to date have had no virus, bugs, malware, etc, issues whatsoever. My main PC has 5 OSs installed, Win7, Win10 and 3 versions of Ubuntu and all 5 run fine with no problems. Win7 and Win10 do run an AV for the little they are used but no AV for Linux.

---

