---
title: "I have a problem uninstalling Ubuntu 8.10?"
date: 2009-04-22
forum: General Help
---

### Post by joekneebone on 2009-04-22
Hey,
Ok I installed windows vista and then installed Ubuntu 8.10 inside windows and now I want to get rid of Ubuntu(to upgrade to 9.4) so I go to uninstall it and I do but when restart my computer it asks me which OS I want and theres 2 Ubuntu's and windows vista so I go to my computer and delete the ubuntu folder and it stills asks me which OS I want? so what can I do to completely get rid of it?
Thanks,
Joe

---

### Post by DagMan on 2009-04-23
It sounds like you need to use whatever tool there is for editing the vista boot loader and just remove those entries for ubuntu.  If the ubuntu space on the vista disk is gone, then you just have two entries in the vista laoder that aren't really pointing at anything but are still causing your boot process to stop and prompt you.

---

