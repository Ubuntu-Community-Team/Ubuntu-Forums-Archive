---
title: "When I have played Flash..."
date: 2012-06-29
forum: Desktop Environments
---

### Post by Azyx on 2012-06-29
..my sound get f*ckt up. What to do?

Flash=Youtobe videos. After that blipping sound appear.

---

### Post by msammels on 2012-07-03
OK, can you please tell me these:

1) What version of Ubuntu are you using?
2) What browser are you using?

If you're using Firefox, I'm going to assume you installed the flashplayer-plugin.

This is no longer support. Adobe have given up on their own Flash player for Linux, and instead Google are taking over, by integrating Flash into their web browser instead. I've used Google Chrome on Ubuntu, and personally had no problems with it, Flash or otherwise.

However, back to your sound: if the problem resolves when you reboot, then there is nothing to worry about. Simply uninstall flashplayer-plugin and possibly Firefox, then install Google Chrome from:

[http://www.google.com/chrome/](http://www.google.com/chrome/)

It has a special .deb file for Ubuntu. Once on Chrome, you should have no further problems regarding Flash.

---

### Post by QIII on 2012-07-03
Flash is no longer being actively developed for Linux.  It is receiving security update support for 5 years.

Firefox is still perfectly functional with Flash for the time being.

Edit:  Sorry, I'm on a train on the way home from work and went in to a tunnel.

Did you recently do any updates?

---

### Post by DMGrier on 2012-07-03
Is there still a open source driver for 64 bit browser for Linux? I remember when I was using 8.04 I was running opera and there was one available back then.

---

### Post by Frogs Hair on 2012-07-03
I don't know about a driver but there is the Lightspark open source flash in the software center. I have not tried it though.

---

### Post by msammels on 2012-07-03
There should be, can't see why not. As far as I was aware the commands were:

```
sudo apt-add-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"

sudo apt-get update && sudo apt-get install flashplugin-installer acroread
```

But I can't remember if that was x86_64 or just x86.

---

### Post by Frogs Hair on 2012-07-03
For Firefox I use this instead of the installer in the software center. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by msammels on 2012-07-03
Haha, wow - that's pretty good. Never seen that one before, who knows, maybe one day Mozilla will start integrating Flash automatically.

---

### Post by QIII on 2012-07-03
Flash-Aid comes from our very own lovinglinux.

---

### Post by DMGrier on 2012-07-03
> **Frogs Hair said:**
> I don't know about a driver but there is the Lightspark open source flash in the software center. I have not tried it though.

LightSpark from what I have read light spark is alpha quality at best. I have thought about sticking with firefox cause I read that a very small percentage of profits from the search engine goes to Canonical but I love my chrome so I do not worry about flash.

---

### Post by Dlambert on 2012-07-03
Chrome (From google) is the only way you will continue to get flash on linux via "Pepper"

---

### Post by Frogs Hair on 2012-07-03
Flash aid will still install 11.2 which will only get security updates .

---

### Post by DMGrier on 2012-07-03
So what is firefox going to do then, will it move to a opensource flash player to stay up to date or will they continue to use Adobe, I just remember it use to use the old flash player that did not always work on 64 bit 8.04.

---

### Post by msammels on 2012-07-03
I could see Mozilla switching to the open source Flash, I doubt they would continue to use Aobe's one, if they stop updating it, even if they continue security support.

---

### Post by DMGrier on 2012-07-04
Lets hope, like I said I remember a time when there was no 64 bit flash support and Firefox continue to use a outdated flash player.

---

### Post by msammels on 2012-07-04
Lol, yeah, I remember those days. Haha, it reminds me of when I needed to use ndiswrapper to install my wireless drivers.

---

### Post by Azyx on 2012-07-04
> **msammels said:**
> OK, can you please tell me these:

1) What version of Ubuntu are you using?
2) What browser are you using?

If you're using Firefox, I'm going to assume you installed the flashplayer-plugin.

This is no longer support. Adobe have given up on their own Flash player for Linux, and instead Google are taking over, by integrating Flash into their web browser instead. I've used Google Chrome on Ubuntu, and personally had no problems with it, Flash or otherwise.

However, back to your sound: if the problem resolves when you reboot, then there is nothing to worry about. Simply uninstall flashplayer-plugin and possibly Firefox, then install Google Chrome from:


[http://www.google.com/chrome/](http://www.google.com/chrome/)

It has a special .deb file for Ubuntu. Once on Chrome, you should have no further problems regarding Flash.

Sorry. It is on 12.04LTS 64-bit and I mostle use firefox, but the problem also  appear when I have used Chromium. The problem disappear after reboot.

How does the update work if you install deb-files? I'm want to avoid install outside apt-get/synaptic/ppa

/Cheers

---

### Post by msammels on 2012-07-04
Well, Google Chrome can update itself from within itself, and it shouldn't affect apt-get update.

---

### Post by Azyx on 2012-07-04
> **msammels said:**
> Well, Google Chrome can update itself from within itself, and it shouldn't affect apt-get update.

Ok. Will try with Chrome, and see, but I doubt that's the problem, cos I have problem with Chromium.

---

### Post by msammels on 2012-07-04
I see. I've never used Chromium myself :) Good luck!

---

### Post by vasa1 on 2012-07-04
> **msammels said:**
> Well, Google Chrome **can update itself from within itself**, and it shouldn't affect apt-get update.
I'm not sure that's correct.
It is true for Chrome on MS Windows and possibly for Macs of which I know nothing but as far as Ubuntu goes, the Chrome updates will be like any other updates. It also means that each update will be full (~30 MB currently) and not differential as happens in Windows for minor updates and this can be a pain for some users accustomed to smaller updates from their MS Windows days.

---

### Post by msammels on 2012-07-04
I stand corrected; thanks vasa1.

---

