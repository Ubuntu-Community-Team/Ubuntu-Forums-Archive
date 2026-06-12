---
title: "Help with GRIP configuration"
date: 2006-01-23
forum: Desktop Environments
---

### Post by stardotstar on 2006-01-23
Hi all,

I have had to rebuild my R51 with Breezy having completely stuffed the networking.

All is well again with my restored configurations and I have been rebuilding my packages to my liking (always better each time you do it)

Now I want to continue using GRIP to encode my cd library and find that none of the encoders are available.  I'm not sure what I added last time to get mp3 ripping happening - I understand that Debian does not package LAME or any mp3 encoders natively because they are not truly free formats, in favour of ogg - i do however need to continue to use mp3.

Can't remember which encoder I was last using but I certainly didn't have to do anything spectacular to make it work.

None of them work - Lame, mp3encode, bladeenc etc...  Cant find the encoder executable.

I have tried to "which lame" etc but they are not installed.  Perhaps I installed something else last time which provided them in advance.

the settings I was using are from this thread [http://ubuntuforums.org/showthread.php?t=110087](http://ubuntuforums.org/showthread.php?t=110087)
from a couple of weeks ago in which [GrammatonCleric]("http://ubuntuforums.org/member.php?u=24155") sorted me out with some encoder and rip settings.

Where to from here?

TIA

Will

---

### Post by stardotstar on 2006-01-24
Anybody?  how to setup the encoders with GRIP??

---

### Post by astoltz on 2006-01-24
lame is in multiverse.

sudu apt-get install lame

---

### Post by stardotstar on 2006-01-25
Thanks very much for that - all working sweet now!

---

