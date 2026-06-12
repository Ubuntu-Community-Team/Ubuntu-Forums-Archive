---
title: "How do I setup LAN gaming on a closed home network?"
date: 2008-06-03
forum: Gaming &amp; Leisure
---

### Post by skew on 2008-06-03
I'm wondering what's required for setting up two Gutsy systems, connected via a wired Ethernet for LAN gaming. Both system also connect occasionally to the internet via their modems through a dialup service (No high-speed available here).  

These two systems are currently networked via openssh and share files perfectly.  SSH incidentally, is the only way I've ever been able to get my systems talking (yes, I'm a network noob).  

Years ago, when is use to have two Windows systems that were similarly connected, I was able to play LAN games such as Quake and Starcraft.  From what I remember it wasn't much trouble setting up those systems for that purpose.  I'm not having a as much success this time around with linux. Granted, I may be using incorrect search criteria in my Google searches but I'm even having trouble digging up just about any information on how to set up my home network for LAN gaming with linux at all.  

 Any help would be appreciated. Thanks

---

### Post by Sammi on 2008-06-03
I'm used to having a router in the mix, which takes care of the networking automatically, so all you have to do is put the cables in.

But doesn't Ubuntu have zeroconfig, that figures network stuff out on it's own if there's no router present? Isn't it enough to just put an ethernet cable between the computers, creating a lan network game on one, and joining the game on the other as usual?

---

### Post by skew on 2008-06-03
> **Sammi said:**
> I'm used to having a router in the mix, which takes care of the networking automatically, so all you have to do is put the cables in.

But doesn't Ubuntu have zeroconfig, that figures network stuff out on it's own if there's no router present? Isn't it enough to just put an ethernet cable between the computers, creating a lan network game on one, and joining the game on the other as usual?


No router in my mix just a simple peer-2 peer system. I tried running a LAN game with Frozen Bubble running on both systems, still no joy. Even with the firewall disabled.  What that game screen reads when a LAN game is chosen is:

*** Please wait, probing for available servers on local network...
*** Unable to probe for available servers on the local network!
*** Network is down/no network?
*** Verify your network setup

So I know the system works as a file server with ssh. Is their some other type of verification I can perform as requested from the message above?

Finally, What is zeroconfig? Do you know of any helpful ubuntu related links to this topic.

Thanks Sammi

---

### Post by dfreer on 2008-06-04
Run the command ifconfig on each computer and post the results here.

---

### Post by skew on 2008-06-04
As always seems to be the case, my request for assistance was a bit premature, Duh!. I got quake2 and scorch3d multiplayer games working across my home LAN last night. I was playing with a lot of settings so I can't with any certainty relate what it was, if anything I did that provided the fix. Anyway, all's well that ends well. 

Still can't get Quake2 with sound on my ALSA driven laptop, but I understand that's a typical problem. 
[
Now does anybody have any suggestions for some good muliplayer linux runnable games?

---

### Post by Dr Small on 2008-06-04
Could you please explain how you got SSH to talk together?
Edit, Sorry there. Just got down to the last post!

---

