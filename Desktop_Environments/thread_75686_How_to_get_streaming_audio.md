---
title: "How to get streaming audio?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by TurdF on 2005-10-14
I just got Ubuntu 5.10 How can I get streaming audio from websites such as talk radio websites?  I'd like to have something that works similar to Windows Media Player but runs under Ubuntu for internet audio.

Thanks

---

### Post by Texas Linux on 2005-11-29
I may be hazy on my instructions, but feel free to respond with any needed clarifications.

I have been working on this problem sine I installed Breezy as I am a San Diego native. I listen to Rock 105.3 KIOZ for San Diego Charger games and 101.5 KG Dave, Shelly & Chainsaw in the mornings. I had to convert to Linux (tired of being bent over by Microsoft), and streaming media is the only way to listen to my favorite morning show!!!

I do know that Mplayer can be installed to play the streaming audio (Windows Media MMS) as well, but I haven't figured it out yet. It is much cleaner as it plays within the little window that Firefox builds when you click to play the streaming audio from your favorite radio station website.

I'm not an expert by any means -- Been using Breezy for about 4 weeks myself.


Try this:

sudo apt-get install vlc

Then get the Firefox plug-in add on at:

[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)

Under Tools in firefox:

Configure the plugin to play streaming by pointing the plugin to:

/usr/bin/vlc

(make sure to click the check box to enable it) 

Good Luck!

---

