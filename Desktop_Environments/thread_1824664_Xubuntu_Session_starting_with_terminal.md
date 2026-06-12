---
title: "Xubuntu Session starting with terminal"
date: 2011-08-14
forum: Desktop Environments
---

### Post by Bazon on 2011-08-14
My Xubuntu Session always started with a blank terminal window and I wasn't able to avoid this with saving a session without a terminal. (as usually proposed.)

I found another cause which I haven't read here yet, so I report it:
It was Orca that caused that terminal window.
I got rid of it by deleting /etc/xdg/autostart/orca-autostart.desktop

Symptom: 
Additionally, the session began with a speech "willkommen bei orca" (welcome to ocra), but that didn't mind me, as it was automatically over in contrast to the blank unusable terminal window without a prompt....

---

