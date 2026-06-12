---
title: "Chrome Remote into Ubuntu"
date: 2022-10-29
forum: Desktop Environments
---

### Post by benjaminbreeg on 2022-10-29
Has anyone managed to remote into Ubuntu 22.04 (or newer) using Chrome Remote? No matter what I do, I keep getting a black screen (see below).
[IMG]https://imgur.com/a/FOBxcej[/IMG][IMG]https://imgur.com/a/FOBxcej[/IMG][https://imgur.com/a/FOBxcej](https://imgur.com/a/FOBxcej)

---

### Post by deadflowr on 2022-10-29
Is it a wayland issue, maybe?
Ubuntu defaults to using the wayland display server.
If you logout and at the login screen select Ubuntu on Xorg and login does the issue still happen?

To select the Ubuntu on Xorg session, 
first, select your username and when the password field shows look toward the bottom right corner and an icon cog should appear.
Click on the cog and it should show entries for Ubuntu and Ubuntu on Xorg,
select Ubuntu on Xorg and click on the cog to close, then enter your password to login.

If you have already tried this disregard.
(And it would have been helpful to post it if you did)

---

### Post by benjaminbreeg on 2022-10-31
Thanks for the reply. I have not had time to investigate this one any further, but I will get back to you as soon as I return to it.

---

