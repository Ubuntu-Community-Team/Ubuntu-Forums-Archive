---
title: "Music Sharing/Banshee"
date: 2006-07-06
forum: Desktop Environments
---

### Post by Kashirigi on 2006-07-06
Hi everyone,

I've installed banshee, banshee-daap and avahi, and enabled music sharing in Banshee.

The problem is that I see no music shares in Banshee, even though I know they're out there. Even weirder is that my other box (running windows as a test) can see my Banshee share on iTunes.

I suspect this may be an avahi configuration problem, although I have no legitimate proof to back this up. Does anyone have any suggestions, or a tutorial for music sharing that I may have missed?

Thank you for any help you can provide.

---

### Post by Kashirigi on 2006-07-06
Well, now I think I've narrowed the problem. I'm using guarddog to configure iptables. Even though I've enabled TCP 3689 and UDP 5353, my shares are still invisible.

When I turn off my firewall, Banshee can magically see Rhythmbox (although the reverse isn't true). 

Can anyone offer some pointers?

Thanks.

---

### Post by Kashirigi on 2006-07-07
Well, I've explored this further.

If my firewall is turned off, I can now see shares on two machines running ubuntu. I'm using guarddog to configure iptables, and  even though the ports are open on TCP 3689 and UDP 5353 when the firewall is up the shares are invisible. What's even weirder is that when I can see the shares (with no firewall), I can't see what they contain, which is not so helpful.

Surely I can't be the only one having this problem.

It's affected both of my ubuntu machines, so unless they're both way out of the ordinary it's probably happened to someone else . . .

---

