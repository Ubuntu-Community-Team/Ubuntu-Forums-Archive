---
title: "compiz 0.8.6 + ubuntu 10.10 + x11. Help is needed"
date: 2011-04-07
forum: Desktop Environments
---

### Post by qazaq321 on 2011-04-07
Hello all
I'm a new user of ubuntu 10.10 and want to clarify something: I have remote linux server and want to launch x11 admin GUI from it using my ubuntu pc.
In winxp it usually going like this - I'm logging in that server, run certain script, and after that new x11 window is appearing with some text and buttons.
Now what is going in ubuntu 10.10 with compiz enabled - after script executing new window is appearing but it's totally empty (only window title is present).
BUT with disabled compiz everything is ok and that GUI is appeared correctly!
Guys is there any options which will allow not to apply compiz to certain applications and it's children ? Or there is another solution.
Thanks in advance!

---

### Post by 3Miro on 2011-04-07
If I understand correctly you have two machines, one with and one without Xorg.

When you get an empty window, have you tried to minimize it and then maximize again?

Once compiz is running, it stands on top of ALL applications. There is no such thing as "apply compiz here but not here". The issue with compiz could be due to the hardware acceleration drivers (I don't know the hardware or the drivers, it can also make a difference if the two machines have different hardware ...) If this is the case, I don't know how to help.

On the other hand, the issue might be with one single simple setting. You can install CCSM (compiz-config-settings-manager) form the Software Center and then you can try to disable some effects and/or enable some "workarounds" to see if this solves your issue.

---

### Post by qazaq321 on 2011-04-07
>If I understand correctly you have two machines, one with and one without Xorg.
Yes, remote is RHEL without xorg, mine is ubuntu.

>When you get an empty window, have you tried to minimize it and then maximize again?
Yes, of course - no sense.

>The issue with compiz could be due to the hardware acceleration drivers (I don't know the hardware or the drivers, it can also make a difference if the two machines have different hardware ...)
I suppose no, because on my colleagues different PC the same thing, once compiz is disabled - everything is ok

>You can install CCSM (compiz-config-settings-manager) form the Software Center and then you can try to disable some effects and/or enable some "workarounds" to see if this solves your issue.
Nope, already tried before...

Last thing that I've tried is to logging in via different server, like this:
ubuntu w citrix client->remote server with Citrix->desired remote server
In this case it's working even with enabled compiz.

---

### Post by 3Miro on 2011-04-07
RHEL and Ubuntu use different versions of Xorg and that may cause problems with the drivers/3D libraries. It would be interesting to see if RHEL + RHEL would give the same trouble, but it would be hard to setup.

Other than that, I am out of ideas.

---

### Post by qazaq321 on 2011-04-08
Unfortunately I can't check mentioned RHEL+RHEL. Anyway, working solution is to use mediation server with citrix.
Thanks for your interest.

---

