---
title: "How to make Conky start last?"
date: 2008-05-07
forum: Desktop Environments
---

### Post by farruinn on 2008-05-07
I've entered Conky into the Startup Programs list under the session manager, but it starts before Nautilus so is covered by the background image. I tried setting its order to 99 under Current Session, then clicking apply but it doesn't keep that setting.

---

### Post by kerry_s on 2008-05-07
for the startup, put->
sleep 10;conky

adjust time as needed.

---

