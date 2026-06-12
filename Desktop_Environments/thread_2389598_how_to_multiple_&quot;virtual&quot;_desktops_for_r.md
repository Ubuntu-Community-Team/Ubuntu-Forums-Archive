---
title: "how to: multiple &quot;virtual&quot; desktops for remote users?"
date: 2018-04-18
forum: Desktop Environments
---

### Post by dgosborn on 2018-04-18
I'd like to have a server that can be used as a desktop by someone physically present, and at the same time 3-4 remote users can access virtual desktops (with or without having their own logins - this is family so sharing disk space is ok).  I don't want to use anything super slow or memory intensive like qemu or vbox.  Suggestions?

---

### Post by QIII on 2018-04-19
Hello!

I'm not entirely sure why you think VMs are super slow when they aren't.  I have 15 VMs on my network using KVM right now on several separate physical machines and can spin up new ones quickly for some purpose.  Not that it matters because that sounds unnecessary for your purposes.

What may be "slow" is the latency associated with connections over wire, which will be the case no matter what remote desktop solution you chose.

VNC comes standard on *buntus, with slightly different front ends depending on your DE.  VNC is a slow technology, so you'll notice it.  You can also look at X2Go, which uses different technology -- NX if I am not mistaken. It's faster, but not so fast as sitting at a local machine. It is far more easy to establish a secure tunnel.  There is also TeamViewer.  KRDP and XRDP work well with Microsoft's RDP protocol.

None of those solutions will be suitable for gaming or watching hi-def video.

NoMahine NX personal version comes close to native performance, but it allows only one user at a time if I recall correctly.

*nixes are by default multi-user, so there is no problem having several users simultaneously logged in and working.

---

### Post by TheFu on 2018-04-19
x2go.

My primary desktop runs in a VM on a 1st generation Core i5 along with ... 8 other VMs.  I access it from the LAN or remotely using x2go. All the VMs work fine.  1 of them is a DVR that handles 2 hidef video recording streams without issues.

Every user with x2go will probably need their own account. I've never tried forcing a new session for every new connection.  Might work, but there would probably be DE config file conflicts.  Having 2 processes accessing the same file when they each expect total control over it often turns out badly.  The default for x2go is for sessions to reconnect, even from different locations, and pick up where they leave off.   Basically, I might be using my desktop at home with 10 windows open, then go to a cafe and reconnect with a laptop picking up exactly where I left off, with running programs still running.

I've seen conferences use x2go as a way to offload screen recording too. I don't know the details, sorry.

---

### Post by SeijiSensei on 2018-04-19
The Linux Terminal Server Project: [http://ltsp.org](http://ltsp.org)

It may be overkill for your case, but it provides what you're looking for.  It's designed for a central server where the users' sessions run and "terminals" where the sessions are displayed.  Users can log in from any connected terminal and see their personal desktop and session.

---

