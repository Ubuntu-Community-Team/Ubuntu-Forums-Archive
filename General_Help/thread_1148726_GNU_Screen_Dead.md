---
title: "GNU Screen Dead ???"
date: 2009-05-04
forum: General Help
---

### Post by ilych on 2009-05-04
This is how my problem arises:
1. Putty into shell account
2. Run screen + sirc (IRC client)
3. Detach screen and logout
4. Putty back into shell account
5. screen -list:

There is a screen on:
        19540.pts-5.comp03     (Dead ???)
Remove dead screens with 'screen -wipe'.

Sirc is still running inside the dead screen (as verified from another machine's irc client). Why does the screen die, and is there anyway to reattach/restore/revive it?

Thanks for any help.

EDIT: Friend solved my problem. I was logging to different servers apparently.

---

