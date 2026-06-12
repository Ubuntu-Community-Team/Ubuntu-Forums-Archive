---
title: "[SOLVED] load kde libs when logging into fluxbox"
date: 2008-09-12
forum: Desktop Environments
---

### Post by Xiong Chiamiov on 2008-09-12
Because plasma drives me nuts, I'm using fluxbox on top of KDE4.  As I'm still using all of the KDE apps, I'd like to have the KDE libs load on login, so amarok doesn't take forever to start, etc.  I ran across how to do this once, but I apparently didn't bookmark it, and can't find it again.

---

### Post by gatewayasteroid on 2008-09-12
> **Xiong Chiamiov said:**
> Because plasma drives me nuts, I'm using fluxbox on top of KDE4.  As I'm still using all of the KDE apps, I'd like to have the KDE libs load on login, so amarok doesn't take forever to start, etc.  I ran across how to do this once, but I apparently didn't bookmark it, and can't find it again.

kdeinit &

---

### Post by Xiong Chiamiov on 2008-09-12
> **gatewayasteroid said:**
> kdeinit &
Thanks, that's exactly right.

For anyone who comes across this while searching, I put that in my ~/.fluxbox/startup.

---

