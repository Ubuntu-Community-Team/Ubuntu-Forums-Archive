---
title: "LightDM freezing occasionally."
date: 2020-01-07
forum: Desktop Environments
---

### Post by hickscorp on 2020-01-07
Hi there, and happy new year!

I've been having this problem for a bit more than 6 months now - with many different versions of Xubuntu. Right now I'm on 19.10.
When I log-into my desktop session (Using LightDM) sometimes nothing happens - the authentication dialog just disappears and it just takes around 6mn to login and segue into the desktop.
When this bug occurs, I am able to get a console TTY and this is what I noticed - there is an additional child process for LightDM in comparison to when it actually works

Here is a screenie of the LightDM process tree using `htop` as `root`:

[ATTACH=CONFIG]284757[/ATTACH]

If I kill the process `lightdm --session-child 17 20` (Itself with two children) then the loading instantaneously resumes and I end up on my session.

Any ideas please?
Thank you very much.

---

### Post by hickscorp on 2020-01-09
Bump, anyone with a similar problem or an idea on how to diagnose please? How would one determine the reasons behind a child `lightdm` process to be spawned in the first instance?

Thanks!

---

