---
title: "Login loop on Ubuntu 17.04 Zesty"
date: 2017-05-15
forum: Desktop Environments
---

### Post by vgorcinschi on 2017-05-15
Freshly installed (3 days ago) I only started having this issue today. I followed the advise to log-in using TTY and did 
`mv .Xauthority .Xauthority.bak`

It worked for the first log-in, but on the next attempt to log-in this "tactic" stopped working.

I have after followed different advice from the following threads:
[LIST=1]
[*]Purge and re-install Nvidia ([https://askubuntu.com/questions/759995/after-upgrade-from-14-04-to-16-04-login-screen-runs-in-a-loop-while-console-logi](https://askubuntu.com/questions/759995/after-upgrade-from-14-04-to-16-04-login-screen-runs-in-a-loop-while-console-logi))
[*]Purge and re-install lightdm ([http://www.linuxslaves.com/2016/05/3-ways-fix-ubuntu-gets-stuck-login-loop.html](http://www.linuxslaves.com/2016/05/3-ways-fix-ubuntu-gets-stuck-login-loop.html))
[*]Do `mount -o rw,remount /` from recovery mode and then `reboot` ([https://www.youtube.com/watch?v=Li-rTbyJLXc](https://www.youtube.com/watch?v=Li-rTbyJLXc))
[*]Change ownership on all files in my home directory (multiple sources)
[/LIST]

Obviously nothing worked (otherwise why would I be writing it). Can you please advise on the fix?

Thank you

---

### Post by voyaflex00 on 2017-05-17
I would try disabling Secure Boot on the BIOS settings. That's what has worked for me.

---

