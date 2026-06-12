---
title: "AnimalJam / Adobe Flash Player"
date: 2016-01-26
forum: Gaming &amp; Leisure
---

### Post by glenberg on 2016-01-26
Hi hope someone can help trying to set up [www.animaljam.com/game/play](www.animaljam.com/game/play) for my kids but it keeps asking me to install Adobe Flash Player witch I do. then try again and it keeps asking me to install flash payer

---

### Post by MikeCyber on 2016-01-27
If you need the latest flash install this after removing other:
Pepper Flash Player - browser plugin
It's in synaptic but I don't remember if that's default or after adding a ppa.

---

### Post by monkeybrain20122 on 2016-01-27
Since Adobe drops support for flash on Linux except for security updates until 2017 your system flash version is stuck at 11.2, that's why your site is not working. You have a few options
1) The simplest is to install [Chorme]("https://www.google.com/chrome/browser/desktop/"), it bundles the latest flash with it.
2) If you don't want to install Chrome and want to use Firefox, install pepperflashplugin-nonfree (it is in the repo, ppa no longer needed), it is the flash extracted from Chrome. Install freshplayerplugin (a wrapper for pepper flash which allows it to be used in Firefox) form the webupd8 ppa with these commands
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin

```
then restart Firefox, go to Tools > Addons, you should have flash20

---

### Post by ajgreeny on 2016-01-27
There is no need for the pepperflashplugin-nonfree any more and it is no longer developed; I recommend that you remove it as well as any other flash packages you have, eg flashplugin-installer.
Install adobe-flashplugin from the canonical-partner repos and in chromium it will give you the latest flash version, 20.0.0.267.

You can also get that same version of flash to work in firefox by installing the freshplayer-plugin from the ppa at [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

---

### Post by yoshii on 2016-01-27
Thanks monkeybrain and ajgreeny.  Both you guys pointed to the same PPA.  
I tried... 
> 
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin


and it installed Flash 13.x instead of 11.x which was helpful for me in getting some sites to work.  
So thanks for that.  And then after that, I removed flash so I wouldn't have two versions going at the same time within Firefox.  

I can't seem to get to 20.x but at least 13.x is better than 11.x

---

### Post by ajgreeny on 2016-01-27
Did you install just the adobe-flashplugin and freshplayerplugin packages?

If you have installed the flashplugin-installer package or pepperflashplugin you will need to uninstall both to get the adobe-flashplugin to give you version 20.0.0.267.

Worth double checking I think.

---

### Post by Buntu Bunny on 2016-01-28
> **ajgreeny said:**
> Install adobe-flashplugin from the canonical-partner repos and in chromium it will give you the latest flash version, 20.0.0.267.

I'm switching from Chrome to Chromium. I started another thread [(here)]("http://ubuntuforums.org/showthread.php?t=2311522&p=13430699") with some questions about installing pepper flash and one answer led me here. 

I already have adobe-flashplugin installed. Are you saying that if I uninstall and then reinstall, Chromium will pick it up so that I don't have to manually install pepper flash (I have 12.04).

No one has answered my questions in the other thread, so getting flash to work in Chromium is not getting any clearer for me.

---

### Post by Dennis N on 2016-01-29
> **Buntu Bunny said:**
> No one has answered my questions in the other thread, so getting flash to work in Chromium is not getting any clearer for me.

Hi Buntu bunny,

After you install "adobe-flashplugin" package from the Canonical Partners repository, all you need to do is restart Chromium and it should detect the newly installed flash plugin and the flash player should work. That's what I have found.

You can test your new plugin and get the version here:
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Also, installing the adobe-flashplugin package removes the old flashplugin-installer package, since adobe-flashplugin installs both versions of the flash player - the Firefox compatable one, and the Chromium compatable one (a.k.a. pepper flash). You don't have to remove it yourself.

EDIT: freshplayer-plugin has nothing to do with Chromium.

---

### Post by Buntu Bunny on 2016-01-29
> **Dennis N said:**
> Hi Buntu bunny,

Hi Dennis N!

> **Dennis N said:**
> After you install "adobe-flashplugin" package from the Canonical Partners repository, all you need to do is restart Chromium and it should detect the newly installed flash plugin and the flash player should work. That's what I have found.

Thank you! That worked!

> **Dennis N said:**
> You can test your new plugin and get the version here:
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

It says

> You have version 20,0,0,267 installed

20.0.0.286 appears to be the most recent, but it's working so I'm not complaining.

> **Dennis N said:**
> Also, installing the adobe-flashplugin package removes the old flashplugin-installer package, since adobe-flashplugin installs both versions of the flash player - the Firefox compatable one, and the Chromium compatable one (a.k.a. pepper flash). You don't have to remove it yourself.

Again, thank you.

> **Dennis N said:**
> EDIT: freshplayer-plugin has nothing to do with Chromium.

And thank you again. I didn't think so, but things like that get thrown in when responders don't read the original question. ;)

---

### Post by MikeCyber on 2016-01-29
removed pepper and installed adobe and am back to:
You have version 11,2,202,559 installed

What a joke. Need back to install pepper to get the latest in firefox.

Back in FF I now have:
You have version 20,0,0,267 installed

---

### Post by Buntu Bunny on 2016-01-29
> **MikeCyber said:**
> removed pepper and installed adobe and am back to:
You have version 11,2,202,559 installed

What a joke. Need back to install pepper to get the latest in firefox.

Back in FF I now have:
You have version 20,0,0,267 installed

Then according to [Adobe]("http://www.adobe.com/software/flash/about/"), you have the latest versions installed. Not sure why that's a joke.

---

### Post by Dennis N on 2016-01-29
> 20.0.0.286 appears to be the most recent, but it's working so I'm not complaining.

It's good to hear you have the plug-in working properly. Expect automatic updates in the future.

So far (to Jan 29), this one (*.286) has not appeared as an update, so nothing is wrong. I have the same one installed (20.0.0.267). In the time I have used this for Chromium, I notice it has taken a few days before releasing to Ubuntu.

---

### Post by Buntu Bunny on 2016-01-29
> **Dennis N said:**
> Expect automatic updates in the future.

That answers my other question (with the answer I want to hear, LOL)

---

### Post by MikeCyber on 2016-01-29
> **Buntu Bunny said:**
> Then according to [Adobe]("http://www.adobe.com/software/flash/about/"), you have the latest versions installed. Not sure why that's a joke.

Yes but with pepper and not with your instructions. Did you even try Firefox?

---

### Post by Buntu Bunny on 2016-01-29
> **MikeCyber said:**
> Did you even try Firefox?

I use Firefox all the time. I'm using it now. I mostly use Chrome (now Chromium) for my blog and Facebook, Firefox for email accounts, and Opera for research. I know some folks would think it silly to keep three browsers open most of the time, but it works for my personal workflow.

---

### Post by Buzz78 on 2016-02-10
I have verified that Animal Jam will run on FireFox using the following instructions on Ubuntu 15.10:
[LIST=1]
[*]Remove existing Flash Player. 
[*]Install pepperflashplugin-nonfree from official sources. 
[*]Install browser-plugin-freshplayer-pepperflash from official sources. 
[/LIST]

No PPA required. :)

---

