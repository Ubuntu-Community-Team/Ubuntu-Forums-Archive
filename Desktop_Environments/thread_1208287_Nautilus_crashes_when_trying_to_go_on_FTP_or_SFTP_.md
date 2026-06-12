---
title: "Nautilus crashes when trying to go on FTP or SFTP directory"
date: 2009-07-09
forum: Desktop Environments
---

### Post by Boten on 2009-07-09
This subject has begun yesterday. The system was last updated 3-4 days ago, but before yesterday everything was good. When I'm trying to go on some FTP dir, it crashes with segmentation fault and with message like this:
** (nautilus:4956): WARNING **: Cannot extract frame (252, 0) from the grid

Of course, I didn't make any changes in GNOME and Nautilus configuration for a long time. How can I fix this problem?

---

### Post by raulih on 2009-07-09
> **Boten said:**
> This subject has begun yesterday. The system was last updated 3-4 days ago, but before yesterday everything was good. When I'm trying to go on some FTP dir, it crashes with segmentation fault and with message like this:
** (nautilus:4956): WARNING **: Cannot extract frame (252, 0) from the grid

Of course, I didn't make any changes in GNOME and Nautilus configuration for a long time. How can I fix this problem?

I've experienced this today on SFTP connection too: nautilus just closes, desktop icons disappear and nautilus has to be started from Alt+F2 to get them back. Happens every time when trying to open SFTP directory. Likewise, no problems previously.

---

### Post by raulih on 2009-07-09
> **raulih said:**
> I've experienced this today on SFTP connection too: nautilus just closes, desktop icons disappear and nautilus has to be started from Alt+F2 to get them back. Happens every time when trying to open SFTP directory. Likewise, no problems previously.

Only recent change I remember, is that I installed Ubuntu One two days ago. Could this be the cause?

---

### Post by raulih on 2009-07-09
> **raulih said:**
> Only recent change I remember, is that I installed Ubuntu One two days ago. Could this be the cause?

Just installed new Ubuntu One related updates in Synaptic, and Nautilus + SFTP seems to work again. See this too [https://bugs.launchpad.net/ubuntu/+bug/395710](https://bugs.launchpad.net/ubuntu/+bug/395710)

---

### Post by blaede22 on 2009-07-10
> **raulih said:**
> Only recent change I remember, is that I installed Ubuntu One two days ago. Could this be the cause?

[s]I'm having this same issue.[/s] I too recently installed Ubuntu One [after I got invited :)]. [s]I'll try[/s] installing the latest updates [s]and see if that[/s] solves it for me as well.

---

