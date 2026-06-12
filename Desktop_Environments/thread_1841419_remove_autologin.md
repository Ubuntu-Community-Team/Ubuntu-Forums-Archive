---
title: "remove autologin"
date: 2011-09-09
forum: Desktop Environments
---

### Post by BushyIII on 2011-09-09
I have an encrypted directory and autologin enabled.  This has now resulted in a loss of my desktop.  I've read posts on fixing this issue but I have a twist that is preventing it from working for me.  

I did the initial installation, and setup the auto login for a different user.  With a recent update my desktop vanished with a host of errors, e.g. cannot update .ICE authority.  

The solutions I read suggested installing LXDE, logging into it and removing the auto login and re-installing gnome.  I cannot do that, I installed LDXE but when I try loggin in the screen refreshes to the the other users login.

Is there a way through Terminal that I can affect the change (remove autologin) when logged in as the other user?

Hope this all makes sense.

---

### Post by Krytarik on 2011-09-09
How about just using the usual GUI way, from within the desktop of the other user!?:

[LIST]
[*]classic Gnome: "System -> Administration -> Login Screen"
[*]Unity: search the Dash for "Login Screen"
[*]Terminal: "gdmsetup"
[/LIST]
Greetings.

---

### Post by BushyIII on 2011-09-10
I'm new and unaware of this option, thanks, I'll give it a try.

---

