---
title: "xdmcp remote session: cannot start new session or take over existing session"
date: 2008-02-08
forum: Desktop Environments
---

### Post by foggydude on 2008-02-08
I use 7.10 on a pc,and want to use my crappy laptop as a client to it. I have the following problem:

[1] cannot open new session over xdmcp
I can reach the host with xming on windows. However: I cannot start a new session: after the login i see only a blank screen with a mouse pointer. But if i login to an account that is also logged-on downstarirs, I do not take over that session, but start with an empty desktop. however, I cannot open programs that are opened allready (firefox, openoffice). In other words: if i want to work on my laptop, i first have to login at the pc and make sure I dont open programs.

[2]how to use gdmflexiserver?
In the "login window administrator" i can chose the option "disallow multiple logins by the same user " (translated from dutch: meerdere aanmeldingen door 1 gebruiker uitschakelen,dont know the orginal).
This looks like the solution. But it says "only works with gdmflexiserver and not with xdmcp".
Is that correct? If so, is there an undertstandablehowto do that, or could you help me with it?

[3]how to move sound?
I dont hear the sound. sounds started remotly are played on the host (funny when playing "robots", scared the crap out of my roommates).

there is very few understandable documentation on gdmflexiserver... would help a lot (if i ever get my radeon and myth working, i might even stop giving up on linux and not install windows with its perfect terminal options)

---

### Post by tcommbee on 2008-02-08
logging in multiple times is still not preferable, as for example firefox will still complain that you have multiple sessions and require to use multiple profiles etc. (those issues are the main reason to disable multiple logins by default imho). i'd rather investigate further, why the normal login hangs. you may check the several logs for any pointers... (EDIT: in login window administrator there is an option to enable debug logging under the security tab)

---

### Post by foggydude on 2008-02-09
Thanks for the response. So it is not normal that i cannot start a new session, that is good to know.

I enabled the logging, as you suggested. Where can i  find the logs that are being made?

What i in the end wouldlike to achieve is like on Windows: if moving from the living room to the bedroom or the lapotp, to continue exactly where i left on the othet client. How can i achieve that? only VNC?

---

