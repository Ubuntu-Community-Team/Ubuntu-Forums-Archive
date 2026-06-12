---
title: "After upgrade to dapper from breezy via synaptic flash won't work"
date: 2006-06-15
forum: Desktop Environments
---

### Post by ajfan on 2006-06-15
I have searched the threads for hours and have tried everything I can find but it still doesn't work.  By not work, I mean will display missing pluggin in all flash sites such as google video, goowy.com, etc.

I have tried to completely remove the flashpluggin-nonfree and have re-installed it via synaptic.  Still doesn't work.  I have tried the "arts" and "none" DSP and neither work.  Flash worked fine for me in Breezy.

I installed firefox 1.5.01 mozilla version not ubuntu version via the threads in breezy prior to my update to dapper.  I also used the thread advising to run sudo firefox from terminal to update to 1.5.04.  This worked successfully also.

So I have an updated dapper, (except gdk-lmlibl and python-soya which won't upgrade), and firefox 1.5.04 mozilla version.

Can someone please give me some ideas what I can try to get this work?

---

### Post by BitTorrentBuddha on 2006-06-16
I use to run my own install of firefox as well, since then I've found the repo version to just be a lot easier, but to install it, you can't use the repo plugin, it will install to the wrong place. Use [this](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW) installer and you should get it working.

---

### Post by ajfan on 2006-06-16
[QUOTE=BitTorrentBuddha]I use to run my own install of firefox as well, since then I've found the repo version to just be a lot easier, but to install it, you can't use the repo plugin, it will install to the wrong place. Use [this](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW) installer and you should get it working.[/QUOTE]

Thank you BitTorrentBuddha.  I downloaded from adobe, followed the install instructions on the adobe site except I ran the intall command as sudo.
When you do the install you have to enter /usr/lib/mozilla-firefox instead of /usr/lib/mozilla.   This was the whole problem I suppose.

Thanks again.

---

