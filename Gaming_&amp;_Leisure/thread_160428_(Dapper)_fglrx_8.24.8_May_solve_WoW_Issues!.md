---
title: "(Dapper) fglrx 8.24.8 May solve WoW Issues!"
date: 2006-04-14
forum: Gaming &amp; Leisure
---

### Post by Toxicity999 on 2006-04-14
For me on my Radeon Mobility 9000 (Dell Inspiron 5100.) I was completely unable to play WoW because of missing textures causing lockups if even loading at all (No button backgrounds or anything! Hmmph!) WELL I followed the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (Method B). And Now WoW Seems to work fine! Anyone experiencing previous issues on my card (or Perhaps others?) Should SERIOUSLY consider upgrading. It's very easy no hacking involved, just a few commands Took me 30 seconds (minus downloading times of course!) In fact... anyone may want to consider upgrading as it seems to be a fairly major release for many people. I'm off to play!

---

### Post by towsonu2003 on 2006-04-14
thanks :) bookmarked to use once it's (dapper) released. 

mobility 9000 is screwing me as well...

edit: does not work breezy with mobility 9000 igp. glxgears report 140 on the average. Was 500 with OPEN SOURCE drivers (sorry for caps, just can't stand this). F**k-faced fglrx driver writers can't do a thing correctly. Thanks for the link though. It should be very helpful for anyone using the thing I'm using now :)

---

### Post by Toxicity999 on 2006-04-15
Could be just complete chance that it helped me. On a personal note... I've been using Dapper since flight 4 and have NEVER experienced any show stopping issues (the occasional annoyance but that's veeeeeeeeeery rare.) You may want to consider just switching now. Realistically there aren't many issues so why miss out on the fun and atleast try. Anyway, there is a breezy version of the guide I assume there no difference majorly anyway... Might want to poke around that instead. Just replace dapper with breezy in that link.

Edit: Ah, and I assume you tried to follow the dapper guide? Yea I don't think that breezy supports this blacklisting feature...

---

### Post by Toxicity999 on 2006-04-15
Bit of an update... I thought I could tweak it out... but I'm still only getting like 5fps tops and degrading from there... I haven't tried playing on cold hardware yet as this laptop is usually on fire by the time I get around to gaming...

---

### Post by towsonu2003 on 2006-04-15
can't try dapper as I'm on dial up (updates... slow connection...). I'll do a clean install when it comes... 

As per the fps, check out ```
cat /var/log/Xorg.0.log | grep DRI
``` If you got what I got, it will say "DRI is not supported for 9x00 cards" or similar. If not, I'm jealous of you ;)

The steps are almost the same. Though I forgot the blacklisting step in the guide. so my fps may be related to that (but X launch was very slow with fglrx + module was tainting the kernel). I just don't wanna tweak anymore, as this time it was hard to clean what ati did to the system. dpkg-reconfigure didn't work. I had to uninstall all the packages (apt-cache search fglrx and remove the last three), copy over an old xorg.conf, and reboot -all from the black command line bc dpkg-reconfigure trashed my desktop by itself-. 

I'm hoping dapper will give a decent fps for me enough not to deal with ati's poor driver writers :)

---

### Post by Toxicity999 on 2006-04-15
I'm on dialup too heh... just get d4x and let it fly a few nights. If you aren't using the line at night I feel it a crime to waste that bandwidth anyway. I always feel just wrong If I'm not downloading something. And yea... DRI works fine for me. Not sure what your issue could of been... did you follow the guide specific to Breezy? It basically consists of the same thing only uninstalling the restricted modules instead of using the blacklisting (as it's new to dapper I guess...) Oh and as for getting dapper the beta freeze begins on the 20th meaning it will start to become more finalized, alot less updating... so wait until they make the first real beta release and you'll get the best of both worls with alot less updates! On average it's only 30mb every few nights for me update wise now. Even on dialup (as we both have I guess. 56k on my part so 5-6k at the uncommon tops.) I understand your wanting to wait but frankly with the beta freeze coming up I think it wouldn't hurt you to bump up if it might mean getting better 3D support. Even if you don't end up with better 3D Dapper itself is infinitely better sofar in my opinion.

---

