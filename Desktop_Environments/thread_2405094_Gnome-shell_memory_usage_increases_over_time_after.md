---
title: "Gnome-shell memory usage increases over time after upgrading to 18.10"
date: 2018-11-01
forum: Desktop Environments
---

### Post by riverfr0zen on 2018-11-01
So memory leak fixes [were part of the 18.10]("https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed") release, but in my case, gnome-shell memory usage seems to have worsened significantly instead after upgrading.

I upgraded to 18.10 from 18.04 via Software Updater (and had previously done the same from 17.10 to 18.04). Since the upgrade, gnome-shell memory usage keeps increasing over time. After ~2 days, gnome-shell appears to use up to 20% of memory (16GB total) and the desktop becomes very unresponsive and pretty much unusable.

Before the upgrade, I could go with months of uptime without this happening, so through some twist I seem to be experiencing the exact opposite of intended effects of the gnome-shell memory leak fixes.

Logging out of Gnome and then logging back in brings gnome-shell memory back down (obviously).

Does anyone have any ideas, and or thoughts about troubleshooting this? Could it be an issue of leftover configs or something from 18.04?

uname -r : 4.18.0-10-generic
gnome-shell --version : GNOME Shell 3.30.1

---

### Post by Autodave on 2018-11-03
It could be just another problem with upgrading rather than doing a clean install.  I have been using ?buntu for 12 years now and I learned a long time ago that upgrading the system usually takes way longer than doing a clean install.  I only use the LTS releases and always do clean installs.

---

### Post by riverfr0zen on 2018-11-27
Bump, as I've discovered I'm not the only one with this problem. Another user has posted about this on [Reddit]("https://www.reddit.com/r/Ubuntu/comments/9tw6cf/1810_gnomeshell_excessive_ram_usage/"). The user continued to experience the issue even after a full reinstall, so it is not an artifact of upgrading from 18.04.

The issue may be related to Nvidia cards--that seems to be one common item between myself and the Reddit user.

Would be great if anyone could provide even some pointers as to how to troubleshoot this, or a link to someplace that does.

---

### Post by perebal-sze on 2019-05-03
I threw my nvidia card away and now using the integrated intel graphic card. The performance is the same, but the memory leak is much smaller (but significant).

---

### Post by speartip on 2019-05-07
Why don't you tell us what is using the Memory? Use top or htop, & post the results back here.

---

### Post by perebal-sze on 2019-05-07
gnome-shell uses the memory. Just one minute ago I had to reset gnome-shell (Alt-F2 r) because it used ~500MB of RAM and it was sluggish. Now it uses ~190MB, and it slowly growing.

---

### Post by perebal-sze on 2019-05-07
5 minutes, and the memory usage increased to 220MB.

[ATTACH=CONFIG]283208[/ATTACH]

---

### Post by swangnation on 2019-05-16
Hi guys, I'm new to ubuntu. Shortly after i got ubuntu up and running on this laptop about 6 weeks ago i started researching grub config because my purple screen would just hang there for 30 seconds no matter what changes i made to grub.

Anyway, i came across 2 articles that specifically stated that gnome shell does have a memory leak and that at the moment, a solution had not been found. For the life of me i can't remember on what websites these articles were on but they were adamant about the memory leak because the problems that were being described are the same as the ones your describing now. I am experiencing the same thing myself, after about an hour of using ubuntu my laptop responds a lot more slower....and slower.

Not sure what the solution is but if you guys can think of one I'm all ears as i am new.

---

### Post by josephmmorgan on 2020-05-14
I know I'm late to this thread, but I've been running 18.04 on my machine for over a year (this was a new machine then), but this issue started with me just this week (5/10/2020).  The only thing I can think of is I installed AppImageLauncher which I since removed, but my gnome-shell goes from 70Mib to 1GiB in 30 minutes. 

I don't have to actually be doing anything and it steadily grows, so I'm restarting it every 30mins to an hour (unacceptable).

The interesting thing is they way it slows down dramatically.  I have 64GiB RAM, so it is getting nowhere near memory exhaustion, and I have 12 core, and also getting nowhere near CPU exhaustion.  Yet, the system acts as if one or both is exhausted.

So, for the meantime, is there a way for me to setup a cron and script to restart gnome-shell every 30mins automatically?

NOTE:  NVM, I found the answer:

     gnome-shell --replace.

---

### Post by coffeecat on 2020-05-14
Back to sleep, ancient thread.

---

