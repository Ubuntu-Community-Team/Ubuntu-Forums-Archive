---
title: "Button &quot;Suspend&quot; not working anymore (LXDE)"
date: 2013-12-17
forum: Desktop Environments
---

### Post by gilga2 on 2013-12-17
Hi!
After upgrading to lubuntu 13.10, I can't put my computer into suspend mode.
What I do usually is: menu "logout" -> button "suspend"

I've tried to edit the menu thanks to an application "LXDE Main Menu Editor", but I don't see any "suspend" entry into that. Nevertheless, I found under "other" a logout button:
Its properties are : 
> Name : log out
command : lxsession-logout
comment : shutdown, reboot or change session

So, on this model, I've created an entry "suspend" : I've put :
> Name : Supend
command : /usr/sbin/pm-suspend

I don't know where the "lxsession-suspend" is (neither "lxsession-logout" by the way).
And needless to say, it doesn't work (but work into the terminal).

Any help?

---

### Post by CitadelUniversal on 2013-12-17
Could you try these instructions [http://forum.lxde.org/viewtopic.php?f=5&t=36125](http://forum.lxde.org/viewtopic.php?f=5&t=36125) - from the lxde forums and report back if it worked.

---

### Post by gilga2 on 2013-12-26
Thanks for your reply CitadelUniversal!

In fact, my LXDE seems to be quite broken so I've decided to give up using the LXDE power manager (xfce4-power manager).

Instead, I'm using pm-utils:
So, when I want to "suspend", I open the terminal and do: > sudo pm-suspend
To be quicker, I've made a shortcut icon inside my LxPanel with the property : > gksudo pm-suspend

And it's not so bad and at least it's working...

---

