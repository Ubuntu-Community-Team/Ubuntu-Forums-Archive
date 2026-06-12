---
title: "Community plasmoid broken"
date: 2011-06-09
forum: Desktop Environments
---

### Post by talmage on 2011-06-09
The Community plasmoid widget thingy is broken on my 64-bit Kubuntu 11.04 system.  The last time it worked was sometime in the 10.04 era.  I will gratefully receive any suggestions for fixing it.

The symptoms are these: 
[LIST]
[*]It opens with three tabs: Nearby, Friends, Messages. I expect this.
[*]There are no entries in the "Nearby" tab.  When I log into opendesktop.org w/Firefox, I can see about a dozen people nearby in my town.
[*]When I click on the configuration button, it shows me my username and obscured password for opendesktop.org.  
[*]When I click on the widget again, it there are more tabs! "Friends" and "Messages" are repeated twice each, giving me seven tabs: Nearby, Friends, Messages, Friends, Messages, Friends, Messages.
[*]When I click on the configuration button again, the username and password fields are empty.
[/LIST]

---

### Post by Zorael on 2011-06-09
It does indeed seem broken.
```
<zorael> Is the Community widget completely broken in 4.6.3? It seems to do nothing.
<annma> hmmm weird I tried it a few weeks ago and it was OK
<annma> how does one knwo he is logged in
<soee> zorael, not sure but it doesnt work for me either
<annma> neither for me
<zorael> :<
<annma> and this login stuff is very unintuitive
<zorael> the number of tabs keep growing, too
<annma> it's broken, damn damn
```
I don't see any "the whole widget is broken" bug entries over on the [list of currently open Community widget bugs](https://bugs.kde.org/buglist.cgi?quicksearch=opendesktop|community) either.

Perhaps it needs to be reported! ;>

---

### Post by talmage on 2011-06-09
I reported it.  It's [bug #275306]("https://bugs.kde.org/show_bug.cgi?id=275306").

---

