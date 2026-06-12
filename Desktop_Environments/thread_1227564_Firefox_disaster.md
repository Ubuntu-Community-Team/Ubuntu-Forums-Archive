---
title: "Firefox disaster"
date: 2009-07-30
forum: Desktop Environments
---

### Post by kelt65 on 2009-07-30
Well, I just had to try Firefox 3.5.1, which I installed in /opt, just to see. I was careful not to update any of my extensions, etc.

After just running it once to take a look, now firefox 3.0.12 (that comes with jaunty) crashes (segfaults) upon opening gmail, after about a second (no time to even switch to html view)

I tried moving my entire profile out of the way and starting clean, but it still crashes.

No errors in the error console.

I've since realized 3.5 is in the ubuntu repositories, and installed that, but it crashes when opening gmail as well. It seems to happen as soon as the chat box loads.

Has anyone had a similar experience?

---

### Post by Katalog on 2009-07-30
I'm certainly no expert, but here are the steps I would take to try and fix the situation. I'd open up the terminal and type:

```
sudo apt-get update
``````
sudo apt-get autoremove
``````
sudo apt-get autoclean
```This would be to make sure that any residual stuff installed by 3.5 isn't still hanging around and messing with your default FF install. Then I'd open up Synaptic and do a reinstall of FF 3.0.12 to make sure that there aren't any missing dependencies and that nothing is deperecated, broken or misconfigured.

My two cents.

---

### Post by kelt65 on 2009-07-30
> **kelt65 said:**
> Well, I just had to try Firefox 3.5.1, which I installed in /opt, just to see. I was careful not to update any of my extensions, etc.

After just running it once to take a look, now firefox 3.0.12 (that comes with jaunty) crashes (segfaults) upon opening gmail, after about a second (no time to even switch to html view)

I tried moving my entire profile out of the way and starting clean, but it still crashes.

No errors in the error console.

I've since realized 3.5 is in the ubuntu repositories, and installed that, but it crashes when opening gmail as well. It seems to happen as soon as the chat box loads.

Has anyone had a similar experience?

SOLVED:

Firefox 3.5 had somehow corrupted the default font I was using - Bit Stream Vera Sans. I switched to Arial and gmail works fine. Nothing else worked. Later, simply reinstalling the ttf-bitstream-vera package fixed the problem with the font.

---

### Post by ugm6hr on 2009-08-01
There is nothing to stop you having FF3.5 and 3.0 installed at the same time.

I am now using 3.5 (aka Shiretoko) as my default browser, but have left 3.0 just in case.

---

### Post by o1e9 on 2009-08-01
It seems the problem remains even I reinstall fonts.  In my case FF 3.0 and Shiretoko 3.5 crash right after opening GMail.  core file leads to Flash Plugin.  Updating libflashplayer.so from 2.0.22 to 2.0.32 does not help.

The problem started few days ago and may be triggered by recommended updates but not sure.  Switching back to 2.6.28-13 kernel makes no difference as some people complained about kernel updates.

Google Chrome 2.0.196.0 has its problems with Flash and no plugins at all.  If I open GMail/GReader and follow and URL then some links may not be opened: new tab/window hangs and I got message from Chrome task manager to kill hanging page.  If I open those links via cut&paste (no GReader/GMail opened) then it works just fine.

---

### Post by Malcy on 2009-08-03
I have exactly the same problem. Firefox 3 and 3.5 suddenly started crashing half a second after opening. When this happens, something has often changed in the system, usually due to an update. I'm moving to Opera until it is fixed.

---

### Post by Colonel Kilkenny on 2009-08-03
I'm having similar problem with Firefox as well. Flash seems to be crashing both 3.0.x and 3.5.x the moment I open a page with Flash. I use Opera so it's not a big problem but annoying still. And Firefox + plugins is really irritating combination to debug.

---

### Post by Malcy on 2009-08-03
Since first posting Firefox has become very crash happy. I'm running 64 bit 9.04 and had the 64 bit flash beta installed.

i have removed the 64 bit Flash 10 plugin and Firefox has become stable again. I don't know why it has suddenly started misbehaving. Since Opera also uses the plugin in the /usr/lib/Mozilla folderflash has stopped working there, though there wasn't any instability with opera.

The next thing is to see if there is a later version of the 64 bit flash 10 plugin.

---

### Post by AlexDudko on 2009-08-03
Though FF-3.0 works if there wasn't a try to install FF-3.5...

---

### Post by Malcy on 2009-08-03
It's both FF 3.0 and FF 3.5

I just downloaded and installed the latest 64 bit flash 10 from Adobe and guess what, the crashes instantly returned. Removing this and installing 32 bit flash via the nspluginwrapper returns things to stability, so this is the way it will be until the issue is sorted. 

I don't think that it is the flash module in itself that is causing the problem, rather that something else has changed to produce a conflict.

---

### Post by Malcy on 2009-08-03
I stripped out traces of previous installs of flash player using the list of commands in this thread:

[http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

Flash player has been updated again, so you will need:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

p.s. I found that my Opera install was using plugins in the Mozilla plugins directory. To give it plugin independence, do the following:

1. Open the /usr/lib/mozilla/plugins folder and copy the plugins. Paste them all into the Opera plugins folder /usr/lib/opera/plugins.
2. In Opera click on Tools,Preferences, Advanced, Content, Plug-in Options..., Change Path...
3. Either deselect or remove the /usr/lib/mozilla/plugins path so that only the /usr/lib/opera/plugins path is available.
4. Click OK and it should show that all the plugins that you copied into /usr/lib/opera/plugins are being used and that this is the only source.

---

### Post by ZaXdude on 2009-08-13
I have the same problem ubuntu 9.04 offered to upgrade mi firefox3, and then shiretoko replaced it, and everytime i use it it close by it self after a minute.

I have 32bits

Please help!!!

---

