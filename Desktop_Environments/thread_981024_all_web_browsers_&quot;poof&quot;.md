---
title: "all web browsers &quot;poof&quot;"
date: 2008-11-13
forum: Desktop Environments
---

### Post by blake82 on 2008-11-13
Hi Folks,

I'm having a really frustrating problem.

For about a week or two now, firefox, and all other browsers I've tried (epiphany and seamonkey) will just randomly quit on me. No warning, no repeatable cause that I can figure out, just out of the blue, "poof" it's gone.

It started around the time I installed wine, and perasive sql for wine.

So I uninstalled pervasive, and uninstalled the gecko component of Wine. No change.

Please let me know if there's anyway I can fix them.

Thanks,

Blake

---

### Post by prshah on 2008-11-13
> **blake82 said:**
> 
For about a week or two now, firefox, and all other browsers I've tried (epiphany and seamonkey) will just randomly quit on me. No warning, no repeatable cause that I can figure out, just out of the blue, "poof" it's gone.


I'm pointing fingers at flash. Here's how to check. Open a terminal (Applications-Accessories-Terminal) and run the browser from that ```
firefox
``` Now you will get a bunch of output in the terminal; use the browser till it blows up, and then post back the last 15~20 lines in the terminal.

It'd help if you also did this with a couple of other browsers.

---

### Post by blake82 on 2008-11-13
Good idea! I hadn't thought of that. Thanks, I'll let you know how it goes.

---

### Post by timjohn7 on 2008-11-14
I've been having the same problem using Opera 9.6 as default and Firefox as alternative.  Same symptoms... unpredictable crash with no obvious symptoms.  I don't believe that it is related to wine as my crashes happened both before & after wine installation & use.
Both browsers restart and recover without a problem, but the problem is disturbing.  I'm running fully updated Ubuntu 8.10 on a Fujitsu Siemens Amilo L6285 with a Gig RAM

---

### Post by blake82 on 2008-11-19
This is still happening very regularly.

I've disabled ALL plugins, but any browser I'm working with, Firefox, epiphany, seamonkey, and opera, will all unexpectedly crash, so I don't think it's a bug with one browser.

This tends to happen when I'm loading a page, but also happens out of the blue.

Is this a problem everyone's experiening, or is it isolated to just a few people???

---

### Post by keithld on 2008-11-19
Have you tried deleting the Default Profile and creating a new one?...

in Terminal: firefox -ProfileManager

I had the problem of Firefox crashing a lot because I imported my Firefox Windows Bookmarks and this fixed it...

I know this may not be the problem your having but deleting & creating a new profile does help with a few problems...

---

### Post by wadelewis4 on 2008-11-19
> I'm pointing fingers at flash. Here's how to check. Open a terminal (Applications-Accessories-Terminal) and run the browser from that

+1

The only time a browser has ever, as you said, went "poof!" and just disappeared on my system, was when Flash went all wonky. Remove flashplugin-nonfree and reinstall. That should fix it right up.

---

### Post by blake82 on 2008-11-19
No, I didn't import a profile from windows

I've uninstalled the flash plugin though...

Hope it works

Thanks!

---

### Post by blake82 on 2008-11-19
Yep... still crashing with flash uninstalled.

It does seem to be triggered by certain pages though.

This one for example:

[http://thehomebased.com/?p=60](http://thehomebased.com/?p=60)

---

### Post by Tomatz on 2008-11-19
Close all browsers

Uninstall **flashplugin-nonfree**

Go here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Drop the dropdownbox (select version to install) and select **"deb for ubuntu 8.04"**

**Download, close browser again** and **install**


Hopefully that will fix the issue ;)

---

### Post by blake82 on 2008-11-19
Very cool!

So far so good! Thanks guys!

Anyone have any thoughts on my other issue?

[http://ubuntuforums.org/showthread.php?t=982425](http://ubuntuforums.org/showthread.php?t=982425)

---

