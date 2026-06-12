---
title: "Can't boot into my own profile (the root user)  &quot;could not write bytes; broken pipers"
date: 2012-08-12
forum: Desktop Environments
---

### Post by MikeDRUBLIC on 2012-08-12
Hello everybody,
 I am stuck  with my xubuntu because it doesn't let me boot into my own user profile  (which is the root). One week ago it didn't allow me to enter to any  profile, and the answer to the login was "stopping v system runlevel  compatibility." SO I checked out the forum, updated the packages in the  Ctrl+Alt+F1 mode and now it allows me to enter as a guest, but not as  the main user, and the answer is "could not write bytes; broken pipers.  Saned disabled."Anybody able to help me? Please be patient, I'm a beginner

---

### Post by Paddy Landau on 2012-08-19
I think you may have a serious problem in that you were using root as your main user. You should never, ever, do that — the security model insists on it.

I'm sorry, I do not know how to solve your problem. The best bet, I think, is to boot into a Live CD; back up *all* your data; and reinstall Xubuntu from scratch.

You may be able to recover your system as follows, but I cannot promise that it will work:

[LIST=1]
[*]Boot into Recovery Mode > Drop to root shell prompt.
[*]Create a new user (I'll assume mike, but you can choose your own):```
adduser --group mike mike
```
[*]Restart (the command to do so is [FONT=Lucida Console]reboot[/FONT]).
[*]Log into [FONT=Lucida Console]mike[/FONT] and see if you can access your data.
[/LIST]

After you have done this, please do not log into root again This is unsupported and, as you have found out, can cause problems.

---

