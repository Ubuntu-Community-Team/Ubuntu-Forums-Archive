---
title: "running nethack in wizard mode?"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by rose34 on 2007-03-26
Hi all,

Have had ubuntu running on my computer for about 2 weeks - love it! have used windows once it that time, the rest has been on linux!

My question is - I've been playing nethack on windows for a few years, and now have it installed on ubuntu 6.10. When I try to run it in wizard mode by using the command nethack -u wizard -D, once it loads up I get told I'm not authorized and need to be logged in as root, which I can't do on ubuntu...

have tried sudo nethack -u wizard -D, no effect. Have also searched these forums, but can't find anything.

Can anyone tell me a way around this problem please? All other linux distros I've tried treat root as a seperate user, but ubuntu doesn't seem to, so what can I do?

Thanks in advance,

Joe

---

### Post by jakev383 on 2007-03-26
> **rose34 said:**
> Hi all,

Have had ubuntu running on my computer for about 2 weeks - love it! have used windows once it that time, the rest has been on linux!

My question is - I've been playing nethack on windows for a few years, and now have it installed on ubuntu 6.10. When I try to run it in wizard mode by using the command nethack -u wizard -D, once it loads up I get told I'm not authorized and need to be logged in as root, which I can't do on ubuntu...

have tried sudo nethack -u wizard -D, no effect. Have also searched these forums, but can't find anything.

Can anyone tell me a way around this problem please? All other linux distros I've tried treat root as a seperate user, but ubuntu doesn't seem to, so what can I do?

Thanks in advance,

Joe

Maybe try:
sudo -s
that will change you to root and maybe it will work then?

---

### Post by rose34 on 2007-03-26
> **jakev383 said:**
> Maybe try:
sudo -s
that will change you to root and maybe it will work then?

just tried that, when logged into the shell as user joe I just type nethack and it begins the game. when logged in as root using sudo -s, I get the message "bash: nethack: command not found."

this happens even when I try running the game in normal mode, but once I logout as root and try as a normal user I can load the game up with no problems.

---

### Post by jakev383 on 2007-03-26
> **rose34 said:**
> just tried that, when logged into the shell as user joe I just type nethack and it begins the game. when logged in as root using sudo -s, I get the message "bash: nethack: command not found."

this happens even when I try running the game in normal mode, but once I logout as root and try as a normal user I can load the game up with no problems.
There's no default paths set for root, so you'll need to define the path to the game. Maybe something like this:
/usr/local/sbin/nethack
As root, do this:
updatedb  (this will take a minute or two)
locate nethack   (or whatever the game's filename is)
That will show you where it's located.

---

