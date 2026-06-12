---
title: "Wesnoth switchs between full screen and windowed"
date: 2008-08-08
forum: Gaming &amp; Leisure
---

### Post by Mega-G33k on 2008-08-08
I've just installed "Battle for Wesnoth" from the Ubuntu repository and it seems to work except it switchs back and forth between full screen and windowed mode when I play. BTW I am running Ubuntu 8.04.

Thanks in advance

---

### Post by Mega-G33k on 2008-08-08
I forgot to mention that I didn't find anything when I searched Google and these forums. Any help would be appreciated.

Thanks

---

### Post by Perfect Storm on 2008-08-08
Disable Compiz should do the trick.

---

### Post by BigSilly on 2008-08-09
That happens when I use Compiz and try to game. Your best bet is to add the Compiz Fusion icon to your panel, so you can switch between window managers as you please. It's in Synaptic as fusion-icon. Hope this helps.

---

### Post by Mega-G33k on 2008-08-09
I will try that and tell you if it works soon, and thanks for the replys I couldn't find information anywhere else.

---

### Post by Mega-G33k on 2008-08-09
Thanks alot, I installed fusion-icon from synaptic and switched to metacity and it fixed my problem.:)

---

### Post by Ozor Mox on 2008-08-09
> **BigSilly said:**
> That happens when I use Compiz and try to game. Your best bet is to add the Compiz Fusion icon to your panel, so you can switch between window managers as you please. It's in Synaptic as fusion-icon. Hope this helps.

Thanks so much for this! I have had Compiz disabled for a while due to it messing up 3D games and having to switch it off all the time, and this has solved the problem nicely for me.

---

### Post by Masterchief3k on 2008-08-09
Hey guys, i just registered because this is one of my very few gripes of ubuntu, but the one that bothers me the most.

Will compiz devs fix this? Can there be a fix? other than switching to metacity, which is an inconvenience. I play lots of games, and like to play at native resolution, which i cannot do unless i am in metacity.

thanks.

What it does for me, and i am sure the same for everyone that this bothers, 3D full screen apps will not let full screen work right, going back to windowed mode and sometimes back and forth, like nexuiz.

---

### Post by BigSilly on 2008-08-10
Masterchief, it's bound to be fixed before long. You have to remember that Compiz is pretty much in its infancy (v.0.60 I believe at the moment) and still working it's way to a proper first release. It's okay to use, but there's some issues still as you now know. Not only that, but other projects have entered the mix (things like AWN), and can make things a bit more complicated too.

None of the above is gospel, it's just my own observations. Please correct me if I'm wrong someone.

So for me, I don't use it just yet. Others prefer to just switch it on and off as they please. Hope this helps (and is correct for the most part!)  :)

---

### Post by Perfect Storm on 2008-08-10
> **BigSilly said:**
> Masterchief, it's bound to be fixed before long. You have to remember that Compiz is pretty much in its infancy (v.0.60 I believe at the moment) and still working it's way to a proper first release. It's okay to use, but there's some issues still as you now know. Not only that, but other projects have entered the mix (things like AWN), and can make things a bit more complicated too.

None of the above is gospel, it's just my own observations. Please correct me if I'm wrong someone.

So for me, I don't use it just yet. Others prefer to just switch it on and off as they please. Hope this helps (and is correct for the most part!)  :)


Aye, that sums it up. It will properly be fixed in future releases.

If people don't want to use fusion-icon to manually enable/disable compiz then make some scripts to the applications/games where its needed. A script that disable compiz - launch the game - when exiting the game starting compiz again.

```
[size=1]
#!/bin/bash 

metacity --replace & 

cd <eg. specific game directory> 
./<binary file/executable file> 

compiz --replace & 
[/size]
```

---

