---
title: "realplayer embedded issues"
date: 2005-12-16
forum: Desktop Environments
---

### Post by linuxgrrl on 2005-12-16
hi,
I am unable to get realplayer to work as an "embedded" player, such as for websites like [http://www.rtve.es/rne/ree/](http://www.rtve.es/rne/ree/)

Error message is: could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

[For other streams that launch a realplayer window, things work fine.]
I have tried all of the other suggestions by others, including: installing realplay using synaptic
getting the latest realplayer rpm and converting it to a .deb and installing; 
using the .bin install script from the realplayer website; and copying or linking all the ram* files from the realplayer plugin directory to ~/.mozilla/plugins.

after each attempt I restart firefox with the same results.
when I try to install the VERY latest realplayer11_***.deb, it fails with a libc++ dependency error.

Help!  I'm starting to feel like an idiot.  Folks went to some trouble to create a linux Realplayer, how come i can't get it to work like everyone else!
thanks in advance
Mary

---

### Post by bronwe on 2005-12-17
I, too, am interested in getting RealPlayer to work to listen to audio files on Amazon.  Right now I'm using MPlayer, but still have problems playing .wma and RealPlayer files.

Any help w/ RealPlayer would be greatly appreciated. 

-bronwe

---

### Post by Redsock on 2005-12-17
Hey all
I'm running the 5.10 gnome and was having trouble with playing different media types...playing all media types, actually.  

Try using automatix, which is a program that installed very easily for me, and then installed every codec and many dvd players, cd rippers etc, and it just works!  Including mplayer integrated into firefox!  you can find more information at this site:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

hope this helps

---

### Post by Redsock on 2005-12-17
(cont)
...Come to think of it my real player doesn't work either and i didn't answer your question at all.  I switched to something that worked more easily...

Also bear in mind that bootlegging these codecs is illegal, they are not FREE, and thus are against the Ubuntu philosophe.

---

### Post by linuxgrrl on 2005-12-18
Thanks, automatix sounds like the right solution except for one teeny problem ...  I'm a bit nervous to try automated scripts because I have mythtv configured and working in my living room ... if I break it, the family may go after me with a pitchfork. [the mythtv newsgroup is full of people who tried "apt-get upgrade" and regretted it.]

So I followed the Unofficial HowTo instructions on getting the mplayer plugin working with the w32 codecs, but even that is giving me grief.  For all windows-based streams, "GMPlayer video" starts (even though the stream is audio only), but nothing happens after that.  Press play, still nothing.

If anyone can suggest how to EITHER 
1.  fix gmplayer so it will properly open an embedded audio stream [apparently once I get that to work, I can copy the RealPlayer codecs to the win32 directory and it will work with embedded realplayer] OR
2.  get embedded Realplayer Gold working properly on its own account

I would be mighty grateful!!  

Thanks - sorry for the long post ...

---

