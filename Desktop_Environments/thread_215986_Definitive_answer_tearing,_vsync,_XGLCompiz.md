---
title: "Definitive answer: tearing, vsync, XGL/Compiz"
date: 2006-07-14
forum: Desktop Environments
---

### Post by saracen on 2006-07-14
I've been looking around for a definitive answer on the tearing issues with XGL/Compiz.  When you move windows around horizontally while running compiz, massive tearing appears on the edges of the windows.  I'm using an NVIDIA 6600GT graphics card.  

If anyone knows whether or not there is a current solution to this problem and could explain it here I'm sure many would appreciate it.  [I found the following post]("http://www.nvnews.net/vbulletin/showthread.php?t=73027") on the NVIDIA Linux forum that mentions using __GL_SYNC_TO_VBLANK=1.  Has anyone tried this?  Does it solve the problem?  where should I put that environment variable?  And what about vsync?

---

### Post by panurge77 on 2006-07-14
Lots of different experiences can be found here:
[http://www.compiz.net/viewtopic.php?id=177](http://www.compiz.net/viewtopic.php?id=177)
I tried it, but I'm not sure it's working as it should. I still get some minor tearing.

I used the /etc/init.d/gdm method. Never tried the macslow script.
I'm also running the triple buffer option on nvidia driver so there's no slowdown

---

### Post by saracen on 2006-07-14
@panurge: Thanks for the link... did it fix your window tearing issues?  Cube doesn't tear anymore but the windows still do the same as before...

---

### Post by Curlydave on 2006-07-14
With ATI you can't even enable vsync.

---

### Post by transm on 2006-07-17
*bump

I'm still having this exact same probelm as well.

---

### Post by kpkeerthi on 2006-07-17
> **saracen said:**
>  Has anyone tried this?  Does it solve the problem?  where should I put that environment variable?  And what about vsync?

It does not work.

---

### Post by oobuntoo on 2006-07-20
I have done alot of searching myself on this issue and, so far, have not come across anyone who has solved this problem. The tearing effect also exists under Windows XP when moving window side-way, no matter what settings I turned on/off for Nvidia graphic card. The only OS that I know of that doesn't have tearing effect when moving window side-to-side is Mac OS X.

The only people, I think, who have answers to this problem might be the xorg, xgl, and/or nvidia driver developers themselves.

---

### Post by Outworlder on 2006-07-30
Well, this is interesting.

I didn't have this tearing before. Now that I added a custom modeline to enable 1152x864@75Hz, the tearing appears. (ATI, btw)

Maybe you guys should keep that in mind. While running more "standard" configurations, the tearing didn't appear.

---

### Post by Anduu on 2006-07-30
> **Curlydave said:**
> With ATI you can't even enable vsync.

Yes you can...there is an app in the repos called driconf that does.I have tried it.

It doesn't completely eliminate the tearing but it helps.

---

