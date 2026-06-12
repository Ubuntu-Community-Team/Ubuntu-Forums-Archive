---
title: "Gnome screensaver lock password problem?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by christian.convey on 2005-10-31
I recently installed Breezy, and one of the users wants to use Gnome.

When the user walked away from a Gnome session for a while, the desktop became locked. When the user returned, he was prompted for a password. (The prompt had a little picture of a dark-skinned guy with a goatee.)

The user's password didn't work to unlock the session. I'm 100% positive the right password was supplied, that CAPS-lock was off, etc.

Does anyone know why I might be having this problem?

Thanks,
Christian

---

### Post by 23meg on 2005-10-31
Were you able to replicate the problem multiple times, or was it a one time thing? Does it still happen with the same user trying to unlock the screen, and with other users?

---

### Post by shapht on 2005-11-15
I recently installed Kubuntu and have the same issue. If I lock the screen in either KDE or Gnome, my password won't let me back in, and I have to kill gdm or just plain reboot to get back up. I am using the 2.6.12.9-k7 from the official repositories as well as a 2.6.14-ck5 kernel i compiled myself(thanks for the howtos on this forum by the way!); the problem exists on both kernels. Any assistance would be greatly appreciated.

<Edit>
Ah, it seems that  sudo passwd <username> did the trick. I was able to change then restore my password, and I can now unlock my screen. The thead(s) about the same issue on the live cd clued me in.

---

