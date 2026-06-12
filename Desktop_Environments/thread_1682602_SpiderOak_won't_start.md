---
title: "SpiderOak won't start"
date: 2011-02-06
forum: Desktop Environments
---

### Post by Findarato on 2011-02-06
I've been a recently new user of SpiderOak, as my Dropbox folder was just getting too big and I didn't want sensitive information to stay unencrypted on their servers. I then went on the search for another service that could give me a little bit more security and found SpiderOak. Their solution is pretty flexible and makes backing up easier even then with Dropbox, as you don't have to keep everything in one single folder.

After a couple of months though, I've had my first problem and thought I'd share it in case someone stomps on the same issue : SpiderOak wouldn't start anymore. There was no specific reason, but it just stopped functioning. I then contacted their support, who were not really responsive (took 2 days for every answer they gave to my e-mails) but I managed to identify the problem : sudo apt-get purge or aptitude purge forgets to delete the .SpiderOak folder in your home folder... This made all my attemps at reinstalling fruitless (always the same result). After uninstalling, removing this folder and then re-installing though, everything is running fine again :).

Hope this helps you if you'r having the same problem.

---

### Post by asease on 2011-02-20
I ran into the same problem and your information fixed it.  Great help, thanks for the post.

Alan

---

### Post by time2spare on 2012-03-13
I also had the same problem and your fix worked.  Thanks !

---

### Post by caelum on 2012-09-10
Same situation, same fix.

---

