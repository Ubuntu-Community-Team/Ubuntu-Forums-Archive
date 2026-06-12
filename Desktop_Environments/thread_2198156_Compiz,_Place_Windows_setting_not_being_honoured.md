---
title: "Compiz, Place Windows setting not being honoured"
date: 2014-01-07
forum: Desktop Environments
---

### Post by wrightflyer-jerrard on 2014-01-07
I am new to the forum.

I am using 12.04 and am trying to get XBMC to startup on a specific viewport (workspace).  So far I have found a few threads which show you how to set it up BUT none of the settings actually work.

I have also tried the settings (created a new parameter in place windows) to start terminal on a specific viewport which does not work either.

Bill

---

### Post by wrightflyer-jerrard on 2014-01-07
I solved it....

I ran this command 
sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

I think I initially ran just the command below

sudo apt-get install compizconfig-settings-manager

Bill

---

