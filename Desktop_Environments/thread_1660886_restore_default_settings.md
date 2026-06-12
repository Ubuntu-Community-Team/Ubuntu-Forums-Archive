---
title: "restore default settings"
date: 2011-01-06
forum: Desktop Environments
---

### Post by sawaal on 2011-01-06
Hi members,

I was using xubuntu 9.04 and recently installed xubuntu 10.04.  I have / partition of size 20GB, swap 1GB and /home of size 80GB. I have only formatted / and install 10.04. I restored the user and member information from my 9.04 to 10.04. When I logged into 10.04, it see my old (9.04) desktop setting and appearance. I would like to restore it to 10.04 default settings and appearance. So I deleted,  ~/.gnome ~/.gnome2 ~/.gconf ~/.gconfd ~/.metacity files and folders and logged out from the user. When I re logged in what I found is my old (9.04) desktop setting and appearance. How can I restore the default 10.04 desktop settings and appearance?

Thanks in advance!
Sawaal

---

### Post by hhh on 2011-01-06
Try deleting .cache and .config? You might want to explore those folders and delete individual items (start with .cache/sessions), or it might be easier to delete the directories entirely and reconfiguring your application's preferences as you use them...

[http://forum.xfce.org/viewtopic.php?id=2824](http://forum.xfce.org/viewtopic.php?id=2824)

---

