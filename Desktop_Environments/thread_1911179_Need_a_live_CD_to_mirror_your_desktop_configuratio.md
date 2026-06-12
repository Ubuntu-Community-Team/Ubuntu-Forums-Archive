---
title: "Need a live CD to mirror your desktop configuration? Find it here."
date: 2012-01-18
forum: Desktop Environments
---

### Post by Kniveau600s on 2012-01-18
Ok so i needed to create a Live CD from an already customized and file loaded Ubuntu. Just couldn't find the right tools and the i bumped into "RemasterSys Backup" which lead me into another search/find/destroy quest kinda like Frodo and stuff (couldn't find all the repository files), into this really beautiful final results. Well, so far no issues!

Hope you find them useful! :popcorn:
January 17,2012:
To create a LiveCD using Remastersys add the below repository since it's not included in Ubuntu's default. Follow this simple steps:

Goto System>Administration>Update Manager:
Find Other Software tab, goto Settings... [password prompt]
Clik on Add... and copy/paste below line:
```
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
```This will add 2 repository lines and one must be deleted due to site being unavailable. Remove the line ending in (Source Code).

Use console to install as normally would:
```
sudo apt-get update && sudo apt-get install remastersys
```After install concludes, goto System>Administration>Remastersys Backup (GUI).

You may now use Remastersys to create a LiveCD! And that is another topic. Have fun!

---

