---
title: "Firefox and Chromium in Linux no thumnails in YouTube page, in Windows OK"
date: 2017-09-17
forum: Desktop Environments
---

### Post by lammert-nijhof on 2017-09-17
I have a strange problem, I don't see the YouTube thumbnails in any of my Linux systems, not on my host Ubuntu 16.04 with Firefox 55 and Nightly Firefox, in the Linux Mint 18.2 VM not in Firefox not in Chromium, in the Peppermint 8 VM not in Chromium and that is true for all my Linux VMs including the betas for Ubuntu, Ubuntu Mate, Ubuntu Budgie and Xubuntu all running Firefox 50 for some reason. In all my Windows VMs I do see the thumbnails in XP, Vista and Win 7 and I run Nightly Firefox, Firefox 52 and Firefox 55. The problem started a few days ago, but then it got corrected, but now it is back again. Why the problem in Linux and not in Windows? Some machines run with 3D disabled and some with 3D enabled. 
What is going on?

---

### Post by vasa1 on 2017-09-17
Are any script/ad blockers active?

---

### Post by lammert-nijhof on 2017-09-18
No I don't use any extensions only "to google translate" and disabling that one has no effect. Strangely enough Ubuntu 17.10 displays the thumbnails again. I first tried it for Chrome and Opera and then for Firefox and all worked well. On the other systems they do not display the thumbnails, the page is not completed and it is waiting for i.ytimg.com, which is where YouTube stores its thumbnails. 
That made me think about a DNS problem, when I changed the DNS settings to 8.8.4.4 it worked again on the host. I changed the DNS setting in the router and now everything seems OK. To be honest I did use a DNS server of another service provider for some weeks in my own router, because it had a higher availability, but that was not valid for me as a foreigner. Probably the Windows machines still used the local DNS setting in the OS and so was Ubuntu 17.10.

---

