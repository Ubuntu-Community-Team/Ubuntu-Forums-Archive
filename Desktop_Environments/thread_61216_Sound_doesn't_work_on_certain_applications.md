---
title: "Sound doesn't work on certain applications"
date: 2005-08-30
forum: Desktop Environments
---

### Post by Captain Crunch on 2005-08-30
First off, I'm a Linux newbie, I'm just getting into it.  So go easy on me.

So far everything is working fine, exept for one problem.  The sound only appears to work on select programs.  The OS sound is fine, I can hear the startup sounds etc.  I can play CDs.  For whatever reason, sound on games does not work, and there is no sound in firefox.

Here is my mobo, it has built in AC97 sound:

[http://www.msicomputer.com/product/p_spec.asp?model=845E_Max&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=845E_Max&class=mb)

Thanks in advance!

---

### Post by racecat on 2005-08-30
Try this:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
restart firefox

I don't know if this is in the Unofficial Ubuntu Users Guide, but be sure to check it out.

Bill

---

### Post by ZosoPage on 2005-08-30
[QUOTE=Captain Crunch]First off, I'm a Linux newbie, I'm just getting into it.  So go easy on me.

So far everything is working fine, exept for one problem.  The sound only appears to work on select programs.  The OS sound is fine, I can hear the startup sounds etc.  I can play CDs.  For whatever reason, sound on games does not work, and there is no sound in firefox.

Here is my mobo, it has built in AC97 sound:

[http://www.msicomputer.com/product/p_spec.asp?model=845E_Max&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=845E_Max&class=mb)

Thanks in advance![/QUOTE]



I had the exact same issue, see this thread, it worked for me....


[http://ubuntuforums.org/showthread.php?t=60314](http://ubuntuforums.org/showthread.php?t=60314)

---

### Post by Lambert on 2005-08-30
Sounds like your hardware is working and you just need to add some multimedia plugins/codecs.

Look at [www.ubuntuguide.org](www.ubuntuguide.org) for some information

Here is a thread on firefox and sound

[http://ubuntuforums.org/showthread.php?t=33107](http://ubuntuforums.org/showthread.php?t=33107)

If you're new to linux the first thing to learn is doing some upfront leg work to solve your problem. You'll get a little more help with some research and knowing what to post. The more work you do up front and more detail you post the more help you'll get.

Some good sites to bookmark are

[www.debian.org](www.debian.org)
[www.tldp.org](www.tldp.org)
[www.ubuntuguide.org](www.ubuntuguide.org)
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

Look for the documentation/support pages. You can google using specific errors or words including linux in the phrase for other sites or just "linux help" to get other sites. You can find a lot of good sites to read starting out.

A good thread in the ubuntu forums for help would be
[http://ubuntuforums.org/showthread.php?t=53050](http://ubuntuforums.org/showthread.php?t=53050)

A lot of good howtos here.

---

