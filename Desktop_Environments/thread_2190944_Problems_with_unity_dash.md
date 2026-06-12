---
title: "Problems with unity dash"
date: 2013-11-30
forum: Desktop Environments
---

### Post by ipet on 2013-11-30
Hello everyone,

This is my first post. I have been using ubuntu for some time. I really like it but I have few problems.
After some upgrade Unity dash doesn't show any app when I search. Each time I reboot I have to restart unity "unity -reset".
It fix the thing but it is really annoying.

Second thing is, I am not sure if it is connected to first issue, but when I login to my account it takes ages to actually start working.
When I try to start some app like google chrome it takes more than 60 seconds to start, same for any other app, and terminal also.

It was all working well before.

My system:
Ubuntu 12.04
4GB ram
i5-3210M CPU
All up to date

Does anyone have solution?

---

### Post by BBQdave on 2013-12-02
**System Settings > Privacy**, I set Firefox Web Browser (**Do not log activity**). For me, it was redundant to have Firefox activity tracked with Dash, as Firefox has it's own search and history function. Dash not tracking Firefox, sped up system response.

You may want to *(Do not log activity)* to applications using the web, as Dash may be waiting on data and slowing your system.

---

### Post by jdeca57 on 2013-12-02
Probably something is broken in the ubuntu-desktop. That's a package, by the way and you can install it with apt-get. Now what I don't get is where that unity -reset comes in. That's clearly a command but since you get no apps in dash and thus no terminal where do you enter it? Is that with Ctrl Alt F1? Anyhow, on that line you could try
apt-get install --reinstall ubuntu-desktop

---

### Post by newb85 on 2013-12-03
Terminal can easily be called in Unity with Ctrl+Alt+T.

---

