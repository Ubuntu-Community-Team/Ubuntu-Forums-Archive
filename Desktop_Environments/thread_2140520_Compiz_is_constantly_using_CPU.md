---
title: "Compiz is constantly using CPU"
date: 2013-04-30
forum: Desktop Environments
---

### Post by cdysthe on 2013-04-30
Hi,

I have two laptops with 13.04 x64 on them. One with nvidia graphics and another with newer Intel graphics. The one with nvidia doesn't have any problems, but the one with Intel has compiz increase it's CPU usage up to around 20% where it stays constantly until I log out and in again. Then it stays at it's normal 3-5% for a while but it's slowly increasing again up to around 20% where it stays. I can feel that the laptop runs hotter than it used to so it's obvious that this constant load isn't good. How can I troubleshoot this and maybe find a solution to it?

---

### Post by grahammechanical on 2013-04-30
What utility are you using to monitor this? I am running top and I do not see that kind of activity with Compiz in 13.04. In fact if the screen is stationery then Compiz disappears from the listing in top only to re-appear briefly as if it is testing if there is screen activity. But then again, I have an Nvidia video adapter and I am running Nouveau.

Some use htop to monitor cpu and memory usage but it has to be installed.

Regards.

---

### Post by cdysthe on 2013-04-30
I'm using htop but double checked with System Monitor. The laptop runs much hotter than it used to also. I've had Ubuntu on it since I got it and it's obvious that it runs hotter and that Compiz is using more CPU than before the update.

---

### Post by Zphyr on 2013-05-20
HI,

I had the same problem, using ubuntu 13.04. CPU was used at 100%! I tried many solutions and after struggling a lot I finally installed Gnome, running it without effects. And everything is fine now CPU use is 7%. 

Hope that helps anyone.

---

