---
title: "Thunderbird url links do not work"
date: 2014-03-20
forum: Desktop Environments
---

### Post by markMDW on 2014-03-20
Hi, My Thunderbird urls do not pop open the default (or any other) web browser.  Instead, the Launch Application dialog box pops open.  desktop.rekong is an option, but when I select it, the Rekong web browser doesn't popup.  I also have Firefox and Chromium installed, but I can't find the executable within the Launch Application's file system directory.  I'm not positive what to look for or where, nor why the desktop.rekong option doesn't work.  I use Rekong most of the time.   This is probably very simply, if I only knew what to do.  Thanks for everyone's help.  In the meantime, I've just been right-clicking on the url links, copying and pasting them into the web browser.  There has got to be an easier way. 

 System:  Kubuntu 13.10 with Thunderbird 24.3.0

[PS-- Everything else about Kubuntu is steller perfection.  I've used Ubuntu and  Xubuntu for past distributions, but without a doubt, for the desktop  Kubuntu is the way to go for me.  It's easy enough, plus far more powerful, versitile and innovative.  Kubuntu has arrived!! ]

---

### Post by speartip on 2014-03-21
When the dialog box opens you need to navigate to /usr/bin/firefox or chromium, then tick the box to use that browser for all http/https links.

---

### Post by markMDW on 2014-04-24
Done.  It works...  Thank You!  :KS

---

### Post by mlnease on 2014-06-12
Hello,

Unfortunately, in my case no dialog box opens at all--when I click on a link, nothing happens.  Can you suggest another approach?  Thanks and in advance.

---

### Post by speartip on 2014-06-13
Open up Thunderbird & go to preferences/preferences/advanced/config-editor.
A warning box will come up but just accept & continue.
Type in the search box "network.protocol-handler.warn-external" without the quotes.
Look for the 3 files ending .ftp .http & .https. Double click each line changing it's value to true.
Close & re-open Thunderbird, then you will be able to follow the advise in #2.

---

### Post by mlnease on 2014-06-13
> **speartip said:**
> Open up Thunderbird & go to preferences/preferences/advanced/config-editor. A warning box will come up but just accept & continue. Type in the search box "network.protocol-handler.warn-external" without the quotes. Look for the 3 files ending .ftp .http & .https. Double click each line changing it's value to true. Close & re-open Thunderbird, then you will be able to follow the advise in #2.  Thanks a million for this, Speartip--it looks like the best advice I've had so far.  Unfortunately, I've already reinstalled xubuntu, TB and FF and all is now well.  I'll mark the thread SOLVED so others can find your suggestions.  Thanks again, all.

---

### Post by Castania on 2014-06-21
This is a persistent problem for a lot of folks . . . and most of the answers don't work.  Even the Mozilla support guys appear dumbfounded.  But this worked for me (Firefox 30, Thunderbird 24.6.0, on Xubuntu 14.04) . . . before I did a complete re-install.   Thanks speartip!

---

### Post by QIII on 2015-05-18
Thread closed.

---

