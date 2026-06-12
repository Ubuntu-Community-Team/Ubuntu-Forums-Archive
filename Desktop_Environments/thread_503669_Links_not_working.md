---
title: "Links not working"
date: 2007-07-18
forum: Desktop Environments
---

### Post by thanuntu on 2007-07-18
Hi everyone,

I am using Kubuntu Feisty on a dual boot laptop (with WinXP).

Suddenly today, all my desktop links (i.e. my desktop config files) started launching their targets with kghostview (!!!). I'm talking about links to /home, to mounted windows partitions (/media/hdxxx), trashcan, to network locations etc.

If I open konqueror, give the url in the address bar, the targets are perfectly accessible.

I tried removing kghostview, but then KDEInit complained of not being able to find this application. I reinstalled it and the problem persists.

I also logged out from X and  removed /home/user/.kde from a shell. Nothing happened, other than losing some panel apps.

Of course I have tried restarting X, or restarting the computer.

Maybe something told KDEInit to start opening links with kghostview ?? The only thing that may be (remotely) related is that I had VMWare share the host computer's network settings (I cannot see how this relates, but it was the only thing I did out of the ordinary, so I mention it just in case).

I appreciate any help,

Thanks

---

