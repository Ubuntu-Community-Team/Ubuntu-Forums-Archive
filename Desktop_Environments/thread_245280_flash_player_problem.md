---
title: "flash player problem"
date: 2006-08-27
forum: Desktop Environments
---

### Post by redmansk8 on 2006-08-27
I have installed flash on two computers no problem. On my third computer which is a new install of Ubuntu I downloaded flash form adobe's site uncompressed and ran install like normal. It installed but it still says I have missing flash plugins when I go to a site that has flash. I also tried this sudo apt-get install flashplugin-nonfree it installs no problem but when you go to sites that have flash it still says missing flash plugins.

---

### Post by lagagnon on 2006-08-27
Flash was already installed and enabled as a plugin for me with Ubuntu 6.06 and Firefox - so I really don't know what your problem is. What version of Ubuntu are you using? Are you using Firefox? Open a new tab in Firefox and check "about:plugins" and see what it tells you about what plugins you have enabled.

---

### Post by dovicka on 2006-08-27
I'm pretty new to ubuntu, by that I meanI installed it just this morning. and i've been trying to get flash player to work with no luck. I copied the two files you download to the plugin folder, and it didn't work and when I try to download it from terminal with sudo apt-get install flashplugin-nonfree it says it cannot be found. some ppl said something about enabling universe... not sure exactly what that means though I checked all the boxes, some which said universe in synaptic. any help would be great cause I love youtube and I need flash

---

### Post by RippyMan on 2006-08-29
> **dovicka said:**
> I'm pretty new to ubuntu, by that I meanI installed it just this morning. and i've been trying to get flash player to work with no luck. I copied the two files you download to the plugin folder, and it didn't work and when I try to download it from terminal with sudo apt-get install flashplugin-nonfree it says it cannot be found. some ppl said something about enabling universe... not sure exactly what that means though I checked all the boxes, some which said universe in synaptic. any help would be great cause I love youtube and I need flash

I'm new to Ubuntu also and I'm getting this exact same error when doing sudo apt-get install flashplugin-nonfree. Does anybody know why it is doing this? I checked all of the boxes in synaptic and it still does this, just like dovicka said.

---

### Post by mgmiller on 2006-08-29
You may have your easiest time by simply installing and running easyubuntu.  It has a flash installer.
Go here: [HTML]http://easyubuntu.freecontrib.org/[/HTML]

Follow the instructions.  It's real easy, you just copy 4 lines of text from their web site into a terminal and hit enter.  You will then have  a nice GUI to pick what you want to install.

Also, be aware that linux only has flash compatibility up to flash7.  No flash 8 or 9 yet.  That is coming soon.  (hopefully)

good luck

---

### Post by Jagot on 2006-08-29
To enable the universe repository see either of these links:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

