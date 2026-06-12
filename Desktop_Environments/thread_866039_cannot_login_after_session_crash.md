---
title: "cannot login after session crash"
date: 2008-07-21
forum: Desktop Environments
---

### Post by alecz20 on 2008-07-21
I'm running Ubuntu 7.10, with all updates, no big modifications.

Every once in a while the Gnome session crashes (Ctrl+Alt+Backspace effect).

After the Crash I am unable to login as that user in another session.

This crash can easily be reproduced by trying to switch users via "Lock Screen" (Super+L).
Sometimes it crashes if I start Diablo 2 with Wine. It alwasy crashes if I try to Alt+Tab from Diablo.
Once it crashed after I started a few applications and switched users using Ctrl+Alt+F(X)

My problem actually has 2 parts:
1) Session is very sensible, when I switch users I keep my fingers crossed hoping it won't crash.
2) After the crash I cannot login on that user, unless I restart the system (the restart fixes the login problem, but is not helpful when I have many users logged in)

Note: no compiz running.
How can I make Gnome session more robust????

---

### Post by Potatoj316 on 2008-07-21
You should be able to have concurent logins of the same user.  Maybe you can disable that, make sure it is enabled if that is possible.

---

### Post by alecz20 on 2008-07-21
So if I log in as the same user on 2 different terminals (tty6 and tty8 for example) when one crashes, I should be able to logout properly on the other one, and then re-login on both...

This sounds like a workaround so I don't have to restart the computer, but I am expecting better from Linux...:wink:

---

### Post by Potatoj316 on 2008-07-21
No, what I was saying is you shouldnt have to log out to log back in.  After one crashes you should just be able to log in again.

---

### Post by alecz20 on 2008-07-21
Well, that is the problem. When i try to login again after the crash I end up staring at an Orange (human color) background and have the cursor. No CPU/HDD activity.
In other words it hangs for that user.

---

