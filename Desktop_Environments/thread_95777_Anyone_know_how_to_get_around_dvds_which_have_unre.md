---
title: "Anyone know how to get around dvds which have unreadable sectors?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Original Brownster on 2005-11-27
Hi,
I have a dvd I want to play and backup on my computer but it will not work. I've tried mplayer, xine, totem-xine (which all play normal commercial dvd's fine as I have the libdvdcss2 library) but all will not play the dvd.
Trying to backup with anything fails because the disk contains unreadable sectors that cause the underlying ripper to stop with an error.

I read somewhere dvd decrypter can cope with this via a plugin that creates a list of the bad sectors then ignores them. Has anyone come across a way of using a native linux tool that will do this please?

Thanks in advance.

---

### Post by Original Brownster on 2005-11-28
* bump *

---

### Post by LittleReinhart on 2005-11-28
Hey,

I have zero experience with DVD-stuff, but maybe the dd-command can help you.

I found a realy interesting article about it a while ago:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=366442](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=366442)

Maybe you could "backup" your dvd with it.

Good luck!

Greetings,
Reinhart

---

### Post by Original Brownster on 2005-11-28
Hi,
Thanks for the reply. You know that might just work, the dd command has a continue on error flag so potentially at least I could create an image first before trying to compress it.

Got to be worth a shot ;)

---

### Post by LittleReinhart on 2005-11-28
You are most welcome ;-)

Greetings,
Reinhart

---

### Post by Original Brownster on 2005-11-29
Hi,
I tried the DD command with the 'conv=noerror' option to continue on errors but it seems to get to a point at around 865Mb then just stops, I tried leaving it for about an hour and it just didnt progress any further.

I've had a good look on the web and found that 'arccos' is Sony's copyright tool that writes unreadable sectors  to the dvd making even playback impossible on the computer - hardly fair.

I might give dvd decryptor a go as this can handle it apparently.

---

### Post by handy on 2005-11-29
Hi,  there is a wonderful piece of software called "isobuster" in the windows world, you can download it & use most of it for free, if you have "wine" or an emulator it may run on linux I can't speak from experience on that.  If you have a friend with an emulator or windows, & it's that important "isobuster" is the best I've seen by miles at recovering data from dvd's & cd's that nothing else will read.
I know, it's on the wrong platform.
Hope it helps, good luck.

handy

---

