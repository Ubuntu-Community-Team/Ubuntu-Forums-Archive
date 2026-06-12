---
title: "Firefox update killed my plugins"
date: 2006-04-19
forum: Desktop Environments
---

### Post by rbrugman on 2006-04-19
Hello,
I installed Firefox 1.5.0.1 with Automatix, but then used the built in updater to update.  After updating, my plugins dont work.  Flash is broken, mplayer is broken - nothing works.  I deleted everything I could find in my home folder and in the /opt folder, but after reinstalling AGAIN nothing works.  I'm wondering if this is a bug or if its me.

Thanks,
Robert

---

### Post by presentt on 2006-04-19
I've never used Automatix, so I'm not sure if the case is different.

However, if you updated from FF1.0 to 1.5, many of the extensions/plugns will not work.  Redownload the plugins, and update your extensions (Tools-Extensions-Find Updates).

Some extensions do not have have updates to 1.5 due to a **maxVersion** tag that was never changed.  It is possible to modify this manually, but I wouldn't recommend it unless you look into the extension first; you risk losing desired data.

Good luck.

---

### Post by rbrugman on 2006-04-19
My extensions seems to be working fine.  It's the plugins such as MPlayer and Flash that don't work.  I tried to reinstall the mplayer-mozilla package as well as the flash package, but they still don't work.  If anyone has a link to how to install firefox manually, I'll give that a try.

---

### Post by presentt on 2006-04-19
[quote=rbrugman]If anyone has a link to how to install firefox manually, I'll give that a try.[/quote] 
Try this: [http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox").

I give credit to **aysiu** for that link when I was trying to set up FF myself recently.  Here's the original thread: [http://ubuntuforums.org/showthread.php?t=161645]("http://ubuntuforums.org/showthread.php?t=161645")

Good luck.

---

### Post by rbrugman on 2006-04-19
I tried that script.  It seemed to work perfectly.  No errors or anything, but flash is still broken, and all mplayer thing (such as movie trailers on Quicktime's website) still say "no picture"

---

### Post by enopepsoo on 2006-04-19
I used automatix and it killed my extensions too.  I just redownloaded them.  You will want to go and take care of some extension related things anyways, like installing the addblock filterset and so on.

---

