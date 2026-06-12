---
title: "Ubuntu 10.04 + fluxbox and slim random crashes"
date: 2012-06-28
forum: Desktop Environments
---

### Post by Yoshiwars on 2012-06-28
Hello all,

I am having a strange issue with a lightweight install of Ubuntu 10.04 on a few PCs. The PCs will randomly crash to a command line login but there is still a mouse on the screen and you can move it until you login with the command line. If you do login and try startx again it says X already running on display 0. I can take a screenshot of that display through imagemagick and its still running right where it left off even though I can't see it.

These pc's are a series of kiosks that I made by using remastersys on a virtual box vm then backed up to the current hardware. I'm using slim and fluxbox on them. All they do is connect via the VMware-view-open-client to our vmware view server through rdesktop. I have seen this happen after the pc is logged in or if you leave slim not logged in for a while. I had this same issue when I used VMPlayer to make the remastered backup. I have looked through the logs in /var/log of slim.log and Xorg.0.log but nothing sicks out. It could be I don't know exactly what to look for.

If anyone could point me in the right direction I would be eternally grateful. I have been googling this like crazy for a while now. I am an intern and the organization really likes the system because I am re-purposing their old hardware for something useful. Thank You in advance!

---

### Post by Yoshiwars on 2012-07-05
Update: I went through and setup another PC from scratch and it has done the same thing. Just once so far after about 5 or 6 reboots. :( I'm glad its not remastersys because that makes setting them up a lot easier for other non linux people.

---

### Post by Rick.B9 on 2012-07-11
*bump

I'm having similar issues with the sttrange crashes.

---

