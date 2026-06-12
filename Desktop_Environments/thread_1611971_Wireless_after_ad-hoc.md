---
title: "Wireless after ad-hoc"
date: 2010-11-02
forum: Desktop Environments
---

### Post by Cl0cKw0rK on 2010-11-02
So i just installed 10.10, and everything was working fine. The main thing to note is that I was perfectly able to connect to wireless networks.

I set up an ad-hoc network, used it, and then shutdown my computer.

Now when I try to connect, I don't see any wireless networks.

Trying to networks that i have connected to previously using the hidden function is a little better. It attempts to connect, but never gets there (never actually connects).

I have tried the power management off thing that some people seem to be having problems with, but to no avail.

The mode on the wireless is set back to managed, so i have not the foggiest what could be going on.

Any help would be appreciated,
Thanks,
Clockwork

Edit: The wireless is working in windows on the same computer.

---

### Post by Cl0cKw0rK on 2010-11-02
For any interested, I found the solution.

Running '#rfkill unblock all' fixed my problem.

---

