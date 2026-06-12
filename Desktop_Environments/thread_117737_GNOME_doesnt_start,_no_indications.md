---
title: "GNOME doesnt start, no indications"
date: 2006-01-15
forum: Desktop Environments
---

### Post by briancurtin on 2006-01-15
i just turned on my laptop a few minutes ago and got the login screen alright, logged in, and it just sits at the brown screen with a mouse cursor. no error message, nothing really showing in /var/log/messages about this problem. i looked around and most other threads dealt with some type of error message being displayed, but im getting nothing.

where else can i check to get things started to get GNOME back? i restarted 3 times, and not once did GNOME come up or display even the smallest message of any sort. i am succesfully running windowmaker right now, but i'd like to get back to GNOME as soon as possible. this is actually kind of cool though, since i used to use OpenStep a while back.

to those that can help: what logs or settings do you guys want? i appreciate any help, since ive never had a problem like this and GNOME problems are brand new to me in the first place.

---

### Post by briancurtin on 2006-01-15
another reboot did nothing again, no indications at all after letting it sit at the brown screen for about 10 minutes. my computer usually boots up incredibly fast  (p4-HT 3.2, 1 gb mem) so i dont remember seeing this brown screen for more than 1-2 seconds before it loads everything else.


edit: i figured it out. well, maybe didnt figure it out, i just ran apt-get install gnome-desktop and it works now

---

