---
title: "Regarding extra repositories...."
date: 2005-04-15
forum: Desktop Environments
---

### Post by denzilla on 2005-04-15
I updated my apt-get with all the extra repositories and everything went great. The concern I have is with the unstable repository. Will the auto update feature in ubuntu see unstable packages from that repository as updates and prompt me to install them? To be specific, these repositories:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

I don't know enough about the update manager or Linux in general to decide if I should trust what it prompts me to update. All I know is that after rebooting, It prompted me to install two updated packages and I did so, without thinking.

---

### Post by shakin on 2005-04-15
Yes, it will find updates from all repositories. You're normally ok if it only updates a couple of packages, but a dist-upgrade could be bad.

As a rule, I only enable the official main and restricted repositories, the backports and extras from the backports project and wine's official repository. I will add other repositories if I need software from them, but I don't keep them enabled and I don't update from them.

The problem with the marillat repositories is that they are for Debian, not Ubuntu. Until Synaptic or apt support some sort of rollback feature (see the Breezy forum) I would rather not risk breaking Ubuntu, as I have done before, by including too many non-official repositories.

---

### Post by denzilla on 2005-04-15
K, I think I'll be commenting those out. I wish I wrote down what those two updates were. Hope nothing is screwed :(

---

### Post by guyforget on 2005-04-16
You probably added that repository for libdvdcss2 which you need to watch dvds.  You could just comment out the unstable entry and use the testing repos...  (testing is the only repo in my sources.list)

---

### Post by denzilla on 2005-04-16
I did get the libdvdcss2 codec. I went ahead and commented out the unstable and the debian repositories. Almost got my first fully configured linux box running and don't want any suprises. I'm not smart enough to fix them yet (will be years). 

BTW, are there no codecs to play aac files? I got all the codecs, but none of the players I have will play them.

---

