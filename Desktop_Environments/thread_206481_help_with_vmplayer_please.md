---
title: "help with vmplayer please"
date: 2006-06-30
forum: Desktop Environments
---

### Post by grooverider on 2006-06-30
hey there ppl, i have the newest ubunut installed, wanted to install vmplayer, tried synaptic anc command line but no luck it always stops saynig this:
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-headers-2.6.15-25 (2.6.15-25.43) ...

Setting up linux-headers-2.6.15-25-386 (2.6.15-25.43) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

anybody has a clue what i have to do in order to get it to work???

---

### Post by harty83 on 2006-06-30
I got similar errors so I just downloaded the install file from vmware's website and used their install tool.  It's really easy.  Just extrat the file then type "sudo [directory where installed]/vmware-install.pl" and follow the prompts.

---

### Post by grooverider on 2006-06-30
thx man worked as you said :D

---

