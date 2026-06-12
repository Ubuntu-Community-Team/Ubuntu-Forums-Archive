---
title: "Gnome not logging in"
date: 2005-05-31
forum: Desktop Environments
---

### Post by teumima on 2005-05-31
Hey guys

My gnome will no longer let me log in. It's weird it was working all great. Then I went to ubuntuguide.org and realised that the extra repos had changed, so I replaced my older ones. Did an update, upgrade, dist-upgrade .Everything worked great. 

A day later. When I would log out by alt +ctrl +backspace, and then try to log in again my gnome wouldn't log in. So I would reboot and then it would work. Eventually it wouldn't work at all. 

I apt-get remove gnome-desktop and then apt-get install gnome-desktop and it would work again, for a few logins, the the same story again.

So...

I apt-get remove gamin (in order to remove all of gnome) and then did apt-get install ubuntu-desktop. Still nothing. 

All I get is the brown ubuntu bg and my mouse pointer, which moves. I waited for a few minutes, still doesn't log in.

Someone in #ubuntu (who seems to know his stuff) told me that he has the same issue and it went away. Like a flue I guess.

Any ideas?

Thanx

-amichai

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=teumima]Hey guys

My gnome will no longer let me log in. It's weird it was working all great. Then I went to ubuntuguide.org and realised that the extra repos had changed, so I replaced my older ones. Did an update, upgrade, dist-upgrade .Everything worked great. 

A day later. When I would log out by alt +ctrl +backspace, and then try to log in again my gnome wouldn't log in. So I would reboot and then it would work. Eventually it wouldn't work at all. 

I apt-get remove gnome-desktop and then apt-get install gnome-desktop and it would work again, for a few logins, the the same story again.

So...

I apt-get remove gamin (in order to remove all of gnome) and then did apt-get install ubuntu-desktop. Still nothing. 

All I get is the brown ubuntu bg and my mouse pointer, which moves. I waited for a few minutes, still doesn't log in.

Someone in #ubuntu (who seems to know his stuff) told me that he has the same issue and it went away. Like a flue I guess.

Any ideas?

Thanx

-amichai[/QUOTE]
 I had seen similar problems being network-related: gnome was waiting for response from a server. This was discussed in these forums before - try searching.

---

