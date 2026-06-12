---
title: "Big Problem With Synaptic"
date: 2007-04-23
forum: Desktop Environments
---

### Post by Georgie-o on 2007-04-23
I am having a heck of a problem.  To start out I am using Feisty and trying get in working a workplace computer.  The firewall has made using synaptic difficult event though I added the proxy settings in synaptic and had I.T. allow the US Ubuntu repositories.  I think what happened is that I got part way into an install of Marcomedia, when it tried to download something from a Macromedia website (which did not work).  Now I have a broken synaptic (when I run it tells me:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Which is bascially useless because when I run the command again it gets hung up, again.  By the way the Synaptic program shows the error and then shuts down, so unless someone can tell me a fix without going in to synaptic, i don't think it will work.

This seems to be a pretty big show stopper.  The system should be made so that small problems like this don't ruin your system.

---

### Post by taurus on 2007-04-23
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Georgie-o on 2007-04-23
When I run the first command I get the following and it hangs up:

Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--16:16:49--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 8.9.120.70
Connecting to fpdownload.macromedia.com|8.9.120.70|:80... 


The Second Command, it also hangs up:

Password:
0% [Connecting to us.archive.ubuntu.com (130.239.18.158)] [Connecting to security.ubuntu.com (82.211.81.138)]

---

