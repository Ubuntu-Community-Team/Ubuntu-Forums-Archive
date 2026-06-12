---
title: "flash not working properly on firefox"
date: 2008-07-08
forum: Desktop Environments
---

### Post by vikramjeet.singla on 2008-07-08
i have installed ubuntu 7.10 on my sony viao...
i have opened youtube to read some tutorials but the videos played in the player were all mess.... :(


thanks in advance

---

### Post by ad_267 on 2008-07-08
Install the package flashplugin-nonfree. Or install ubuntu-restricted-extras which includes other stuff you will most likely want. You might need to enable the universe and multiverse repositories by going to Settings - Repositories in Synaptic Package Manager and reloading package info.

---

### Post by vikramjeet.singla on 2008-07-08
thanks for the reply AD...
i totally newbie in linux....
however i have searched on google to install flashplugin-nonfree using following steps:

enabled multiverse and restricted repostories

then execute following command

sudo apt-get install flashplugin-nonfree

but it says no package information is available... :(
please help

---

### Post by nycste on 2008-07-08
> **vikramjeet.singla said:**
> thanks for the reply AD...
i totally newbie in linux....
however i have searched on google to install flashplugin-nonfree using following steps:

enabled multiverse and restricted repostories

then execute following command

sudo apt-get install flashplugin-nonfree

but it says no package information is available... :(
please help

ur thinking to much

1. open synaptic package manager
2. input password if asked
3. hit search
4. type "flashplugin"
5. install the only option that pops up "flashplugin-nonfree"
6. problem hopefully solved

just trying to be helpfull my second post ever !

---

### Post by dixonstalbert on 2008-07-08
try command

sudo apt-get install update

this will update your repository database so apt can find package. then re-try  sudo apt-get install flashplugin-nonfree

---

### Post by vikramjeet.singla on 2008-07-09
thanks for quick reply...
i have got chance to perform these steps...
however now the place where flash should have been placed is totally blank... :confused: .....
please help...

---

### Post by jwkolberg on 2008-07-10
I had the same problem and could never get the non-free flash to work. If you install the vlc mozilla plugin, which is also in synaptic, pretty much any online media works perfectly.

---

### Post by IronArjen on 2008-07-10
Just by chance do you have a 64 bit machine? In that case flash is not available (that's what you get with commercial software). However, Kilz wrote a script that allows you to install a 32 bit version of Mozilla that does include Flash, Java and Adboe reader. Goto the next link and good luck.

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

---

### Post by CraigPaleo on 2008-12-31
> **IronArjen said:**
> Just by chance do you have a 64 bit machine? In that case flash is not available (that's what you get with commercial software). However, Kilz wrote a script that allows you to install a 32 bit version of Mozilla that does include Flash, Java and Adboe reader. Goto the next link and good luck.

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

I just read the how-to. It says it's obsolete as both flash and java are working in 64 bit. That's good to know. I might be upgrading to 64 bit!

__________________
[Raw Paleo Diet]("http://www.rawpaleodiet.com/index.php")

---

### Post by Rohan Kapoor on 2009-01-01
> **IronArjen said:**
> Just by chance do you have a 64 bit machine? In that case flash is not available (that's what you get with commercial software). However, Kilz wrote a script that allows you to install a 32 bit version of Mozilla that does include Flash, Java and Adboe reader. Goto the next link and good luck.

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

Flash has been working in 64bit since Ubuntu 8.04 on my machine!

---

