---
title: "mandi (interactive firewall of mandriva)"
date: 2005-11-21
forum: Deferred/Invalid Requests
---

### Post by towsonu2003 on 2005-11-21
I got the idea from: 
[http://www.ubuntuforums.org/showthread.php?p=510359&posted=1#post510359](http://www.ubuntuforums.org/showthread.php?p=510359&posted=1#post510359)

and the firewall looks very nice as well:
[http://ubuntuforums.org/showthread.php?t=93222](http://ubuntuforums.org/showthread.php?t=93222)

and the rpm is supposedly here (I could not access it): 
[http://rpm.pbone.net/index.php3/stat/4/idpl/2252905/com/mandi-ifw-0.7.4-1mdk.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/2252905/com/mandi-ifw-0.7.4-1mdk.i586.rpm.html)

[Edit] 
Appearant reason I could not access was firestarter blocking it as follows:
Time:Nov 21 21:15:07 Direction: Unknown In : ppp0 Out: Port:47009 Source : pantera.pbone.net Destination:10.21.93.24 Length:1420 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 21 21:15:07 Direction: Unknown In : ppp0 Out: Port:47009 Source:193.25.186.51 Destination:10.21.93.24 Length:1420 TOS:0x00 Protocol:TCP Service:Unknown

I am not sure if this malicious or not...

Seems to be okay according to this: [http://www.seifried.org/security/ports/47000/47009.html](http://www.seifried.org/security/ports/47000/47009.html)
Just wanted to make sure you all know about this.
[/Edit]

Maybe I am missing the interactiveness of ZoneAlarm?

Also, I am aware that this is not already in repos, but as it seems so nice, I wanted to give it a try, knowing that you (hopefully) won't bite...

---

### Post by uberlinux on 2005-11-21
It is a two part item:
The 'Mandi' daemon, and,
The mandi-ifw, which appears to be the rules.  
Mandi, just appears to be a dbus monitoring daemon.

---

### Post by jdong on 2005-11-21
Something this core-level I'd like for the Ubuntu team (or even MOTU) to do it... Try to get in contact with Ubuntu devs about this one.

---

