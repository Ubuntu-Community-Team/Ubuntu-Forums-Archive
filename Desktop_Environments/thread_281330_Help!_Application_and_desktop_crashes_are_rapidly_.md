---
title: "Help! Application and desktop crashes are rapidly making my computer unusable"
date: 2006-10-20
forum: Desktop Environments
---

### Post by DarkStarDeity on 2006-10-20
Further to [this post]("http://www.ubuntuforums.org/showthread.php?t=280229"), I have just been "reminded" *grumble* that there are a couple of other applications on my system that are crashing regularly - notable nautilus and update-notifier. 

There is no pattern that I can see except that they often (but not always) occur after a period of inactivity with the application. gnome itself takes me back to the login window if I leave my computer idle for more than about 10 minutes.

The update notifier by itself crashes every couple of days, gnome any time I leave the system idle for more than about 10 minutes, but a crash of one or more of these applications is happening several times an hour. The firefox crashes are becoming so frequent (often 3 or 4 times an hour) that I am installing opera to see if that is any more stable.

Please help! I am rapidly losing faith in my decision to switch to linux.

---

### Post by hanzomon4 on 2006-10-20
Quick questions.

1.version of ubuntu are you using edgy or dapper
2.have you installed some apps that are not in the ubuntu repos.
3.have installed compiz or beryl
4.What kind of cpu do you have
6.Which kernel are you running

I'll help in whatever way I can, and most problems are "fixable" trust me ;)

---

### Post by DarkStarDeity on 2006-10-20
Whoops! I should have given that info in the initial post

1. Dapper
2. I have Cisco VPN installed (but not running most of the time and hasn't been run in a while), QEMU (ditto), Clickomania and transport tycoon (games) and I just installed Flash 9 for Firefox (but the problems started well before this).
3. No
4. Pentium 4, 3.0 GHtz
5. The latest - 2.6.15-27-386

Edit: I'm pretty sure the problems started soon after the last kernel upgrade.

---

### Post by DarkStarDeity on 2006-10-30
I was going to update this post and say that, after a bit of educated guesswork, I turned off my screensaver which has increased the stability of my system. I haven't had a crash in nautilus, update-notifier or gnome since I did it, just after the last comment on this post. And firefox has not crashed either - until tonight, when I've had three crashes in half an hour :( But until tonight, turning off the screensaver seemed to have done the trick. And I can still lock the screen manually (which starts the screensaver), so it isn't the screen saver itself. Rather, it seems that whatever is polling for system activity is causing applications to crash.

I don't know why Firefox has just started playing up again though :(

---

### Post by foxmulder881 on 2006-10-30
Corrupt install or your installation doesn't like your vid card maybe? How long has your current OS install been on your machine?

---

