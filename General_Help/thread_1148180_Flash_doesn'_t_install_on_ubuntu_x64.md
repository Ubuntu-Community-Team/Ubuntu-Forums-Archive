---
title: "Flash doesn' t install on ubuntu x64"
date: 2009-05-04
forum: General Help
---

### Post by stefangr1 on 2009-05-04
I have just installed Ubuntu 8.04LTS x64, and I have a problem with getting flash to work.

When I try sudo apt-get install flashplugin-nonfree, I get the following output:

The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 118877 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--10:15:47--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.34.70
Connecting to fpdownload.macromedia.com|88.221.34.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:15:49 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

It seems that the location where the pluging has to be downloaded no longer exists!

I also tried some scripts to install flash 10, but they run into an error related to libnss3.so, which is encountered by quite a lot of people.


What should I do...???

---

### Post by docjones2 on 2009-05-04
download the file at this location
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

and extract it to ~/.mozilla/plugins

.mozilla is a hidden directory, so it may not appear in a file browser or via ls.

make the directory if it doesn't already exist.  This will only intsall the flash plugin for firefox, which 9/10 is all you need for flash anyway.  If you're looking for a standalone flash app like in windows, I do not know what you would do, but that's not really necesary, since you can just open swf files in firefox with this plugin.

---

### Post by delcypher on 2009-05-04
You could try manually installing the plug-in from [here]("http://packages.ubuntu.com/hardy/amd64/flashplugin-nonfree/download")


You could (just an idea, it's probably not recommended though) also try the alpha version of the x64 linux plug-in 


[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Installation instructions are [here]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install")

---

### Post by docjones2 on 2009-05-04
> **delcypher said:**
> You could try manually installing the plug-in from [here]("http://packages.ubuntu.com/hardy/amd64/flashplugin-nonfree/download")


You could (just an idea, it's probably not recommended though) also try the alpha version of the x64 linux plug-in 


[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Installation instructions are [here]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install")

I have this alpha plugin working on 2 seperate 64 bit machines, one of them a laptop, both of them came out of the box with windows (one of them with vista) and it works without any difficulty.  It actually worked better than the flash plugin I had on a windows 7 machine.

---

### Post by stefangr1 on 2009-05-04
Thank you all so much!

Just unpacking the provided x64 .so to a directory was a lot easyer than my previous attempts, with all those scripts that you first have to check to see whether they're safe to run or not.

And this works :)

---

### Post by madhavvk on 2009-05-04
Try this:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

It worked for me!

with best regards,

Madhav.

---

