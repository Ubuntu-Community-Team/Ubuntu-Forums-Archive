---
title: "Sauerbraten questions"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by Kashirigi on 2006-07-18
So, Sauerbraten runs nicely on my laptop, which is somewhat surprising seeing that's it's not exactly cutting edge.

When I go into Multiplayer and attempt to get the server list, I get nothing. Either there are no servers listed on sauerbraten.org, or, more likely, I need to configure the firewall.

I wasn't able to see which ports needed to be opened on Sauerbraten.org, so I thought I would ask here.

Thanks for any help you can supply.

[edit]
Now I'm not so sure it's the firewall. I disabled it, and tried to connect to the master server list. I got this:

looking up sauerbraten.org...
sending request to sauerbraten.org...

And that was it. Nothing came back. Any suggestions?

---

### Post by Kashirigi on 2006-07-18
Well, I've partially solved the problem. I had to forward some ports on my router (so no playing, say, elsewhere).

If I turn off my firewall (using guarddog), all is well. However, I'm not so keen on this solution. I've opened ports 28785 and 28786, but guarddog is still blocking.

So, not being exceptionally well versed in linux, I have these questions
a) Which ports do I need opened for Sauerbraten, besides the two above? If you don't know the answer to this, how about
b) Where are the logs from guarddog/iptables kept, so that I can check the logs and see what I need to open?

Thanks very much for your help.

---

### Post by Sp00ne on 2006-07-19
Are you looking through the listof games, that are local, or internet?

---

### Post by Kashirigi on 2006-07-19
It was internet games. And by the way, I've now solved the problem. If you're using guarddog, make sure that under Protocol/Game, Direct Play Gaming is checked off, in addition to allowing the two ports mentioned above.

If you're behind a router that you can't configure for port forwarding, you're of luck. Eg, coffee shop network, campus network.

I hope my experience helps someone.

---

