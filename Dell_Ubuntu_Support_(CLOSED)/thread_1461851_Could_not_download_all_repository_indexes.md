---
title: "Could not download all repository indexes"
date: 2010-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zander1013 on 2010-04-24
hi,

when i run the update manager i get a message that says "Could not download all repository indexes"

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

> Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

this started after an attempt to update the system last monday. perhaps it is a side effect of the medibuntu servers down last week?

please advise.

---

### Post by garyedwardjohnston on 2010-04-24
Try this:

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by zander1013 on 2010-04-25
hi,

i have the sources.list now looks like this...

> #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/)  main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) -security main restricted universe multiverse 
deb [http://....archive.ubuntu.com/ubuntu/](http://....archive.ubuntu.com/ubuntu/) -updates main restricted universe multiverse 



flashplayer isn't working even after following instructions to install it.

wait a minute i had not selected a country. let me try that.

its a dell mini 9 that shipped with ubuntu 8.04. before last week everything worked.

---

### Post by zander1013 on 2010-04-25
i am still having trouble.

the update finishes cleanly but i can watch content at hulu anymore.

please advise.

---

### Post by snowpine on 2010-04-26
Hi Zander, /etc/apt/sources.list is an important system file; please do not edit it unless you understand exactly what you are doing, and always make a backup of this file so you can restore if you make a mistake. (look for a file called /etc/apt/sources.list~ if you have it you're in luck :)) repogen was, to put it bluntly, an irresponsible suggestion. :(

dl.google.com is not a "stock" software source for the custom Dell version of Ubuntu (you must have added it for some reason?), and Google does not support your LPIA architecture. If you remove this line and restore sources.list to the factory default, you should be able to install Flash with 

```
sudo apt-get install flashplugin-nonfree
```

Sorry, but I haven't used Hulu before; can't help with that.

(edit) I found a copy of the Dell default sources.list, hope this fixes the problem for you: [http://www.mydellmini.com/forum/ubuntu-netbook-remix/122-sources-list.html#post1800](http://www.mydellmini.com/forum/ubuntu-netbook-remix/122-sources-list.html#post1800)

---

