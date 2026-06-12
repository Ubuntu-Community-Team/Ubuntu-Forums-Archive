---
title: "Flash causing all browsers to crash"
date: 2009-03-05
forum: General Help
---

### Post by Pitot Heat on 2009-03-05
Ive been using Ubuntu 8.04 for a couple weeks now and after doing some research on this OS, I feel Im getting a fairly good handle on it. However, one aspect that baffles me is in regards to flashplayer. So far, the only version I have gotten to work correctly is 9.0.159 while the earlier 9 version and all subsequent versions of 10 do not work. When installing version 10 nothing I do allows it to install and trying numerous solutions found throughout the forum no joy either. Curiously, in Synaptic, I notice that the updated version of Adobe-flash is different than the version of flashplugin. Im not able to update these to the same version even when allowing for updates of unsupported updates in software sources. Ok fine, flash 9 seems to be manageable if I use the correct version of it, but lately a couple sites cause the webbrowser to crash (firefox, galeon, Epiphany all crash at the same sites). I have determined the problem is directly due to flash as when I uninstall flash the pages do not crash. However, sites such as youtube do not cause any crashes (yet....) which makes it even stranger... Sorry for the length of this post and thanks for your help!

Edit: I just installed mozillaflashblockplugin stops the crashes at least until I click on the offending video... Any work around this? As of this morning even these videos played with no problem....

---

### Post by ajgreeny on 2009-03-05
I don't know if you have already done all of this, but I suggest you remove completely (purge) all your current flash packages, make sure you have the **ubuntu partner repos** enabled and then install the *adobe-flashplugin*.  If you have tried this already, sorry, but I don't know what else to suggest.

It seems very important to purge all previous versions of flash before installing the adobe version from the partner repos, and I just wonder if you have done this.  It may even be worth rebooting between, though I don't think it is necessary.

Just out of interest, what are the sites that make flash crash for you.  If you post a link I will try them out on my 8.04.2 fully updated system and see if I get the same problem with flash 10.0.22.87-2 from synaptic.
PS:  also remove *libflashsupport* if it is installed as it is not needed for flash 10

---

### Post by Pitot Heat on 2009-03-05
Thanks for the quick reply! I've tried purging it like you have suggested a couple times without success. I have flashlibsupport installed as its the only way I have found to get sound while running flash9. Fore example COmedyCentral's videos have begun to cause crashes with flash 9.0.159 today.

---

### Post by ajgreeny on 2009-03-05
Comedycentral's flash videos work well for me so there must be some other problem with your system.  Try without compiz running to see if that helps ```
metacity --replace
```  Perhaps the video card in your box is your problem; what card do you have and what driver are you using?  I have an ati 9200SE, great with the open source driver used automatically when I installed.

---

### Post by davisch on 2009-03-05
I am having the same problem.  I just installed Flash 10.o r22 and it seems to work fine on most sites but some just crash Firefox.  For example this one -

[http://www.huffingtonpost.com/2009/03/05/jon-stewart-eviscerates-c_n_172057.html](http://www.huffingtonpost.com/2009/03/05/jon-stewart-eviscerates-c_n_172057.html)

I can see the things on YouTube just fine but this site - and a few others just load most of the page and then Firefox just closes?

---

### Post by davisch on 2009-03-05
I see Comedycentral also crashes Firefox for me.  I have an Nvidia graphics card and driver.

---

### Post by ajgreeny on 2009-03-05
Your huffingtonpost site works for me with no problem, so perhaps it really is the nvidia graphic card or driver that is the problem, whereas my ati card and driver (radeon) is OK.

---

### Post by Pitot Heat on 2009-03-05
The Huff post is where I first noticed the problem too. I have a mobility radeon 7500 but it seems its unsupported by Ubuntu so its just the basic video driver. Im thinking it has to do with the specific type of flash being used by some sites since this all of a sudden happened where as before it was fine.

---

### Post by davisch on 2009-03-05
I see the problem with nvidia is documented - but not fixed - on the adobe site.

[http://bugs.adobe.com/jira/browse/FP-1069](http://bugs.adobe.com/jira/browse/FP-1069)

---

### Post by davisch on 2009-03-06
I installed Epiphany and get the exact same results.  It crashes the same way Firefox does.  Has anyone installed updated drivers for an Nvidia card to see if it changes anything?

---

### Post by martrn on 2009-03-06
I have the very latest nvidia drivers binary installed (from nvidia) and flash and yes the huffington post (as always) crash firefox.

I can give you a list of many strange flash sites but (they all) would crash my browser with adobes flash player installed.

Flash player for linux is a bit buggy.

---

