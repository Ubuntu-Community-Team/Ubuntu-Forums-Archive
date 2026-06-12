---
title: "Firefox CPU hog using DownloadThemAll"
date: 2009-04-22
forum: General Help
---

### Post by netmask254 on 2009-04-22
I'm downloading a Fedora DVD (4.7GB) to desktop with 5~6MBps speed, using DownloadThemAll of Firefox 3. I found that CPU utilization of Firefox process (by "top") is around 50% during download, meanwhile I have only 1 blank webpage opened. After downloading is finished, the CPU utilization becomes normal (<5%). I installed Ubuntu 8.10 amd64 via Wubi on Thinkpad X61S (2 cores with 1.6GHz, 2G RAM, 160GB 7200rpm disk). 

I guess there may be two possible reasons for the high CPU utilization: 
1 DownloadThemAll uses special methods to achieve high speed but in cost of CPU load. 

2 Ubuntu Wubi has a poor disk write performance. I notice that when I'm copying large file from Ubuntu to a different Windows XP disk, the maximal copying speed is only 7~8MBps. 

Does any body encounter similar issue before or can give some explanation? Thanks very much!

---

