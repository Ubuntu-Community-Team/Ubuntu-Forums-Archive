---
title: "Adobe flash player not working in Ubuntu"
date: 2008-12-08
forum: General Help
---

### Post by deneth on 2008-12-08
I facing a huge problem as adobe flash player doesn't work in Ubuntu. I have updated the packages list with apt-update and still doesn't work. I have already tried gnash and neither its working as well.

[http://ubuntuforums.org/showthread.php?t=634126](http://ubuntuforums.org/showthread.php?t=634126)

[http://ubuntuforums.org/archive/index.php/t-641035.html](http://ubuntuforums.org/archive/index.php/t-641035.html)

I have tried both these former threads but both leaves to dead ends. When i try to reinstall i get the message that its already installed. But both Firefox and opera doesn't recognize it. 

Any help.

---

### Post by nothingspecial on 2008-12-08
Try following this

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sandyd on 2008-12-08
hint: i'm not at home right now so i can't check this out... but
i faced this a while ago

type this in and note the errors in the terminal. Then install the libraries that are needed

cd /etc/firefox*3*
./firefox

Then go into firefox and go to about : plugins

(no spaces in between about : plugins)

Then look at the terminal errors. Install the libraries that it says it can't find

---

### Post by deneth on 2008-12-11
> **nothingspecial said:**
> Try following this

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I tried this as explained

"sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree""

But the terminal says those libraries are not installed so cant be removed. In addition says 
"E: Couldn't find package nspluginwrapper"

---

### Post by deneth on 2008-12-11
> **carlee said:**
> hint: i'm not at home right now so i can't check this out... but
i faced this a while ago

type this in and note the errors in the terminal. Then install the libraries that are needed

cd /etc/firefox*3*
./firefox

Then go into firefox and go to about : plugins

(no spaces in between about : plugins)

Then look at the terminal errors. Install the libraries that it says it can't find


Tried this 
inside firefox*3* directory there exits no executable. So doomed.

---

### Post by nothingspecial on 2008-12-11
> **deneth said:**
> I tried this as explained

"sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree""

But the terminal says those libraries are not installed so cant be removed. In addition says 
"E: Couldn't find package nspluginwrapper"

Just try ```
sudo apt-get install flashplugin-nonfree
```
that should get flash working.

---

### Post by deneth on 2008-12-15
I did as told and what happened was 

> Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--18:58:51--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving cache.mrt.ac.lk... 192.248.8.106
Connecting to cache.mrt.ac.lk|192.248.8.106|:3128... connected.
Proxy request sent, awaiting response... 404 Not Found
18:58:53 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


I think the flash tar ball couldnt be downloaded. Is there any way to resolve this

---

### Post by charanpreethu on 2008-12-15
I am facing the same problem....Please someone help us to get the flash player workin..

---

### Post by deneth on 2008-12-16
Seems like no help is arriving for settling this matter. I have tried the help of some friends. And most of them replied they even have the same problem. Even some had installed it the flash player is not funtioning properly. It had displyed contents only in few sites. 

I guess we can have a proper aid on this.

---

### Post by nothingspecial on 2008-12-16
I`ve always done it the other way but try this
```

sudo apt-get install adobe-flashplugin
```

From [this]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Adobe_Flash_Player_for_Firefox_Plug-in")
guide which you may find useful for other stuff.

---

