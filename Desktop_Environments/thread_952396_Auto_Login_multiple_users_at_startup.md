---
title: "Auto Login multiple users at startup"
date: 2008-10-19
forum: Desktop Environments
---

### Post by noodles90210 on 2008-10-19
There is option in GDM config dialog to allow auto login, but only for one user. I need auto loging for me and my wife. Solution would be to allow GDM config to add more users for auto-login. Is there any temporary work around? This way we must auto-login one of us and second user must enter password each time computer is started, which is annoying and makes auto-login itself useless. ](*,)

---

### Post by sethvath on 2008-10-19
May I ask why do you need to log into 2 accounts at the same time upon startup? Your wife uses the same computer at the same time as you? I am aware there are systems with 2 monitors, 2 keyboards and they share a single cpu. Is this dual sharing system you're using? If not you could always make a script to log on your wife's account after auto-logging into your own. Add the script to sessions.

---

### Post by steveydoteu on 2008-10-19
Indeed, a script would suffice. Automagically log one account in, add the script to your sessions to log in the second.

---

### Post by driftingprogrammer on 2009-10-26
Can anybody help withwhat the script would look like.

Thanks.

---

### Post by alastairpetrie on 2009-12-02
Sorry no help from me but wanted to add my voice to this request. 

This is a feature I've been looking for for so long.

Ideally for me it would be just mouse click on the desktop switcher on the Gnome panel to get to the other user. But I'd settle for another user being logged in automatically on a different terminal if that can't be done.

Either way my wife would be far more likely to use Linux (if I set her user up with all the programs that she wants, her email account, etc) rather than demand a PC with Windows on. It's just too much hassle for people who don't care about computers to want to spend any time configuring it or logging in to a different account.

Anyone got any ideas?

Thanks

---

### Post by multiple on 2010-01-29
I can think about a few reasons for why one would use two or more accounts.
If you configure an account for one user but at the same time need to be logged in at your account.

Or if you want to try out another windowmanager such as kde,fvwm....

Or simple, as the creator of this thread want - switch user with his wife, they trust in eachother so no need for password, but they want their own personal environments.

Here is how to get it done, sort of - maybe other people will contribute to polish it.

***
First you log in as yourself, then you use the fast userswitcher app to let your wife log in and this time she need to enter password just once - after that switch back to your account with ctrl-alt-F7, and because the fast user applet made you logout so you need to enter your password once, but - and here it is *because your wifes account never logged out - then you can use it again without any pass if you hit ctrl-alt-F8 (or in some cases ctrl-alt-F9)*
After that neither you or your wife need to use password again. As long you switch with the ctrl-alt-Fx combination
***

The best solution would be if one could get the system not ask for password for more than one user should, then you need to set the autologin to one of the users, which is what i think the creator of this thread originally meant.

---umop ap!sdn----

---

