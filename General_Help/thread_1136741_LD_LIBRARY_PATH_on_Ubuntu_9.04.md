---
title: "LD_LIBRARY_PATH on Ubuntu 9.04"
date: 2009-04-25
forum: General Help
---

### Post by lixo1 on 2009-04-25
Hi everybody,

I have a big problem, today I installed Ubuntu 9.04 (wubi) and I tried to add a LD_LIBRARY_PATH to my .profile file.
the command is:
export ROOTSYS=/usr/share/QtRoot/root
export LD_LIBRARY_PATH=$ROOTSYS/lib:$LD_LIBRARY_PATH

Now, when I login, I tape printenv on the bash and the LD_LIBRARY_PATH is not set!!!!
How is it possible? This same 2 lines on .profile, have been working perfectly on the last 3 Ubuntu versions!
If I do: source .profile, it works!
Thank you very much for any kind of help,
Cheers,
Louis

---

### Post by scientist47 on 2009-04-27
I replied to your other post:
[https://bugs.launchpad.net/ubuntu/+bug/366728](https://bugs.launchpad.net/ubuntu/+bug/366728)

---

