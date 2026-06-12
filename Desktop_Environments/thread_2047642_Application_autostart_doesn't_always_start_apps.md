---
title: "Application autostart doesn't always start apps"
date: 2012-08-25
forum: Desktop Environments
---

### Post by gilson585 on 2012-08-25
Ok this is driving me absolutely bonkers. I use a desktop as a DVR and compile myth from git. I don't use a service to run the backend just a simple entry in session and startup to run it once logged in. Naturally the system starts on it's own while I'm not around to record TV but myth doesn't always start, wtf? I can even run myth from cmd line when it fails to autostart with no issue. Can't find anything in the logs either, not that I know where to look either other than syslog and dmesg. If it makes any difference it's autostarted as root and the sudoers file has been edited to be able to exec sudo w/o a prompt. Please don't tell me how I shouldn't do that cause I already know the dangers. Or that I can't run myth as root, cause root has the same privileges as the user myth and the logged on user so it works just fine. Although I get the feeling this is where the issue is stemming from. If you must know I run as root so that it may use r/t threads where needed and higher priority threads where it sees fit. For some reason it wouldn't do so if run as normal user.

---

### Post by Toz on 2012-08-25
> just a simple entry in session and startup
Just to confirm, this is the login user's session startup, right? (Not root's)

> but myth doesn't always start
So sometimes it does autostart?

On the occasions that it doesn't autostart, have a look at the ~/.xsession-errors log file (hidden file in your home directory) - it may provide a clue as to why it isn't starting.

---

### Post by gilson585 on 2012-08-26
Yea it's the user's autostart not root's.

It started happening some months ago but since my favorite recordings are coming back in Sep it has to get fixed lol.

I would check the xsession log but I have gone off in what seems like the completely wrong direction. I have followed some tip for setting up systemd to handle running the backend. Little did I know Ubuntu doesn't support it but I was already too far in so you guessed it, I installed it and now have some other quirks to work out. This might not end well.

---

