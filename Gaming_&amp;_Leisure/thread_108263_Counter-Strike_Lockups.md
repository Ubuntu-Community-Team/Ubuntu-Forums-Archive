---
title: "Counter-Strike Lockups"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by Evil Whisper on 2005-12-25
Hello,

I'm having some issues with wine, I've tried the one from the ubuntu repository.  I've tried wine 0.9.3 and I've even compiled wine 0.9.4 from source.


Ubuntu Wine:  Steam installs and runs sort of OK but it periodically locks up for  30 - 220 seconds.  In random intervals.  Mostly on the server choosing screen.

Wine 0.9.3: Steam installs and runs alright but it also periodically locks up for 30 - 220 seconds. In random intervals.  These lockups can occur anywhere.

Wine 0.9.4: Steam installs and does not run.  It just segfaults and dies...  It also dumps a bunch of junk in "hex" in the console.


CVS Cedega: Same as wine 0.9.4...

Wine also uses all of my swap: 1.5gb.

I've also installed the Mozilla Active X control I found on linux-gamers.net


Does anyone have a solution to fixing these lockups I really wanna play CS again.

Thanks in advanced,
- Evil Whisper :D

---

### Post by pharcyde on 2005-12-25
This looks like a known issue after the recent steam update issued on December 22, 2005.   I've been seeing the same issue on my own wine/steam install.  I'm currently using breezy with wine 9.3.  I've checked further into the issue and it seems other people are seeing it as well.  Below is a bug track report from winehq.

[http://bugs.winehq.org/show_bug.cgi?id=4131](http://bugs.winehq.org/show_bug.cgi?id=4131)

I don't know if this is a wine implementation issue or some buggy code in steam.  My assumtion is the problem relates to the steam update provided by the following link.

[http://www.steampowered.com/index.php?area=news&id=496](http://www.steampowered.com/index.php?area=news&id=496)

---

### Post by Evil Whisper on 2005-12-25
Thank you for the information pharcyde.

[http://www.ubuntuforums.org/showpost.php?p=603498&postcount=5](http://www.ubuntuforums.org/showpost.php?p=603498&postcount=5)

I've posted a patch here that fixes the segfaults in wine 0.9.4 but steam still freezes.

---

