---
title: "[SOLVED] HELP! Ubuntu 7.10 has locked me out"
date: 2008-12-10
forum: General Help
---

### Post by shelbyvision on 2008-12-10
I've been using ubuntu 7.10 on the same computer for about 8 months, always with the same user name and password. I usually put it in hibernate mode when I'm not using it. last night I turned it on from hibernate, and when I typed in my password, it told me it was incorrect. I retried several times, same result. I rebooted it, same result. I have no idea what has happened here or how to fix it. Any ideas?
Thank you,
Steve Shelby

---

### Post by taurus on 2008-12-10
Boot into recovery mode from GRUB menu and at the prompt, change your password.  Assuming your login name is steve, run

```
passwd steve
shutdown -r now
```
Now, see if you can log in with your username and the new password.

---

### Post by shelbyvision on 2008-12-10
Thanks Taurus, for your reply. 
It has turned out to be a hardware problem, not ubuntu (my apologies, ubuntu).
I need a new keyboard!
Steve

---

