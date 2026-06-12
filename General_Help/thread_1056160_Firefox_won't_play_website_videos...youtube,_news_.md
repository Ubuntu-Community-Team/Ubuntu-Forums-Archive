---
title: "Firefox won't play website videos...youtube, news websites"
date: 2009-01-31
forum: General Help
---

### Post by Ahren75 on 2009-01-31
Can anyone help?

---

### Post by overlord.gaurav on 2009-01-31
Have you installed the flash plugin for firefox ?

---

### Post by Ahren75 on 2009-01-31
in the add/remove applications -

Flashblock extension for Firefox *mozilla extension that replaces flash plugin by a button *

is marked installed.

Is that what you mean?

---

### Post by Gizenshya on 2009-01-31
no, thats just an add-on that blocks annoying flash ads.

Are you using 64-bit or 32-bit?

and 8.04, 8.10, or what?

if you're on a 32-bit version, go here -> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

if you're on 64-bit it's a bit more complicated...

---

### Post by MarblePanther on 2009-01-31
Flashblock is an extension that *blocks* you from viewing flash--the exact opposite from what you want.  I suggest you just install "ubuntu-restricted-extras" package in Synaptic Package Manager.  It will install flash and more like java, dvd-playback, codecs, etc...

---

### Post by utnubuuser on 2009-01-31
If you have the flashblocker enabled, all you get is a little icon where the flash video should be.

To play flash video embeded, disable flash-blocker, and install flash-plugin non-free through synaptic.

---

### Post by thriftee on 2009-01-31
go look at the sticky in the multimedia section.  it shows how to get all the video formats working.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Ahren75 on 2009-01-31
> **Gizenshya said:**
> no, thats just an add-on that blocks annoying flash ads.

Are you using 64-bit or 32-bit?

and 8.04, 8.10, or what?

if you're on a 32-bit version, go here -> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

if you're on 64-bit it's a bit more complicated...

Hi I'm new to Ubuntu..I'm on Hardy Heron - dunno if it's 8.04 or 8.10...or 64 bit or 32 bit...how do I check?

---

### Post by MarblePanther on 2009-01-31
Open up Synaptic Package Manager (under System, Administration) and click the search button and type: ubuntu-restricted-extras

then install it by right clicking on the entry and mark it for installation, then hit the apply button at the top
 also uninstall flashblock

---

### Post by Gizenshya on 2009-01-31
Hardy Heron is 8.04.

and if you don't know, then you're almost certainly using 32-bit.

so, you can choose ".deb for ubuntu 8.04+" from the list on that site and install the firefox flash player only.

Or, you can do what some recommended above and install lots of other video codecs (coders/decoders) as well.

---

### Post by Ahren75 on 2009-01-31
Thanks Everyone! I just recently gave up Windows for Ubuntu - so far it's been positive. I learnt alot from y'all just from one little question.

Problem solved it was following MarblePanther's below.


> **MarblePanther said:**
> Open up Synaptic Package Manager (under System, Administration) and click the search button and type: ubuntu-restricted-extras

then install it by right clicking on the entry and mark it for installation, then hit the apply button at the top
 also uninstall flashblock

---

### Post by MarblePanther on 2009-01-31
Glad to help, pm me if you have any other problems

Good luck and happy Ubuntu-ing!

---

### Post by Hr_Birnbaum on 2009-02-26
Unfortunately, I have the same problem, however, installing "Ubuntu Resticted Extras" didn't help.
Any other suggestions?

> **MarblePanther said:**
> Glad to help, pm me if you have any other problems

Good luck and happy Ubuntu-ing!

---

### Post by wochti on 2009-02-26
This happened to me after an update of the flash player yesterday......

solved by going to adobe site to install flash player 10 plugin for firefox (ignore warning that says there is an updated version in repos) then when the update came up again, this time update went fine.

---

