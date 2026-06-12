---
title: "problem running saba centra"
date: 2009-03-04
forum: General Help
---

### Post by midododo11 on 2009-03-04
hi
i have ubuntu 8.10
and i have classes on the internet that i must use a program named
Saba centra that create a virtual class
website
[http://www.saba.com/products/centra/](http://www.saba.com/products/centra/)
and i must pass that system check to run it
[http://eplace.nmsu.edu/SiteRoots/main/index.jhtml?default=true&domain=/](http://eplace.nmsu.edu/SiteRoots/main/index.jhtml?default=true&domain=/)
but i cant run it on ubuntu i tried wine but didnt work
plz help me

---

### Post by midododo11 on 2009-03-04
nobody can help?

---

### Post by midododo11 on 2009-03-04
up up

---

### Post by midododo11 on 2009-03-05
nobody at all can help no moderators experts anything ?????!!!!

---

### Post by crokett on 2009-03-05
If it is a Windows App and you can't or don't want to run it under Wine, then either dual boot with Windows or install a Windows virtual machine under Ubuntu.  Google VirtualBox.

---

### Post by garijon on 2009-09-18
Hey were you able to solve this problem ?
I tried wine but it didn't work.
Then I found an rpm for version 7.6, I used alien to convert it to a .deb file and install the .deb.
I logged in but firefox complained there was a missing pluggin.
Has anyone been able to solve this issue ?

Regards,

---

### Post by Rud91 on 2009-10-27
Hi @ all

I'm also new here in this forum and with linux/ubuntu.

At first. sry for my bad english, i'm from germany ^^


Ok the problem you have here is not a problem with saba centra. it's a problem with firefox.
i'm using ubuntu 9.04 (i386) and after the install, the update installs a update for firefox with a plugindir. at /usr/lib/firefox-3.0.14 (in my case).
the saba centra deb package installs the plugin a /usr/lib/firefox/plugins ... so what must you do:
Copy the plugin in the new version of firefox.
> sudo cp /usr/lib/firefox/plugins/npCentraUpdaterPlugIn.so /usr/lib/firefox-3.0.14/plugins/restart firefox... and look at extras > addons > plugins ... in my case their can you find "CENTRA UPDATER PLUGIN"

My problem now is, how to configure pulseaudio so that it works with headset. at this time the test-language is very fast, like fast forward at a videoplayer. 
where can i find a how to for configure pulseaudio??

dirk

---

### Post by Pirindingo on 2010-10-03
> **Rud91 said:**
> Hi @ all

I'm also new here in this forum and with linux/ubuntu.

At first. sry for my bad english, i'm from germany ^^


Ok the problem you have here is not a problem with saba centra. it's a problem with firefox.
i'm using ubuntu 9.04 (i386) and after the install, the update installs a update for firefox with a plugindir. at /usr/lib/firefox-3.0.14 (in my case).
the saba centra deb package installs the plugin a /usr/lib/firefox/plugins ... so what must you do:
Copy the plugin in the new version of firefox.
restart firefox... and look at extras > addons > plugins ... in my case their can you find "CENTRA UPDATER PLUGIN"

My problem now is, how to configure pulseaudio so that it works with headset. at this time the test-language is very fast, like fast forward at a videoplayer. 
where can i find a how to for configure pulseaudio??

dirk

Hi Rud, where or how do you download the saba centra deb package? Tks a lot!!

---

