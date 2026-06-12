---
title: "Don't upgrade to the lastest libcario2 version 1.4.10-1ubuntu4.1"
date: 2007-12-06
forum: Desktop Environments
---

### Post by scubajeff on 2007-12-06
The lastest version 1.4.10-1ubuntu4.1 will break your system, would not allow you to log into gnome, xfce or enlightenment. If you have already upgrade to this version like me, downgrade to version 1.4.10-1ubuntu4 will solve the problem.

```

sudo apt-get intstall libcairo2=1.4.10-1ubuntu4

```

---

### Post by serfcx on 2007-12-06
> **scubajeff said:**
> The lastest version 1.4.10-1ubuntu4.1 will break your system, would not allow you to log into gnome, xfce or enlightenment. If you have already upgrade to this version like me, downgrade to version 1.4.10-1ubuntu4 will solve the problem.

```

sudo apt-get intstall libcairo2=1.4.10-1ubuntu4

```

Anyone else had this problem ?

---

### Post by stalkier on 2007-12-07
> **serfcx said:**
> Anyone else had this problem ?

I am current on upgrades and have had no problems. However, I do not use enlightenment. Perhaps that is the problem???? (I could be wrong):confused:

---

### Post by serfcx on 2007-12-08
Nobody else has mentioned this problem.
maybe this is a ´hoax´ post :confused:

---

### Post by gentoofrm on 2007-12-08
Thanks, scubajeff!

This is NOT a HOAX at all.

This bug was already reported:
[https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861]("https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861")

My GNOME panels, Firefox and GEDIT that use some Asian TTC and TTF fonts (Microsoft) just crashed immediately after I upgraded to the latest libcairo2.

If there's no problem on your system, you don't need to downgrade.

After I downgraded as scubajeff mentioned, everything is okay!

---

### Post by scubajeff on 2007-12-10
I didn't mention that I use Chinese at the first post. Because at that time, I was not aware that the bug is Asian Font related. It's really a pity that there are still so many programmers out there who do not pay enough attention to i18n support. :confused:

---

### Post by bluetick on 2007-12-10
Hi. 

I don't use any Asian languages, and I was affected by this bug. In my case, my left handed mouse settings were still there, but the buttons were set up like a right-handed mouse. I got an error message that I can't remember or find in the logs, but the gist of was that a GTK process hadn't started when I logged in. 

I did the downgrade, and now it's all good. 

If you don't mind, here's a correction for a typo: 

[INDENT]sudo apt-get install libcairo2=1.4.10-1ubuntu4[/INDENT]

Thanks for the info. I found the cause of my problems about 2 minutes after I started to look for it here. I think I'm going to like Ubuntu, after using Red Hat/Fedora, Mandake/Mandriva, SuSE, Debian, and probably a few I can't remember.

---

### Post by rrwo on 2007-12-22
no problem with it

---

