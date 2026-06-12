---
title: "[SOLVED] Avant and startup title bar glitch"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by theonlykman on 2007-06-11
Hi,
Every time I reboot I get (screenshot).
Obviously, the avant title bar is not desired.
I figure its happening because beryl hasn't completely started by the time avant gets going.

So, I was wondering if someone could show me the ropes with creating and using a startup script that will make AWN be the very last thing to startup, or at least startup after Beryl. If anyone has any alternative solutions that would be appreciated as well.
Thanks

---

### Post by theonlykman on 2007-06-11
nevermind, figured it out on my own :D

---

### Post by PaulFXH on 2007-06-11
@theonlykman
I ocassionally get the problem you describe (maybe once or twice per 100 restarts). When it happens, I just shut down AWN and start it again which gets rid of the title bar.
If you have a more elegant solution, I'd love to hear what it is.

---

### Post by theonlykman on 2007-06-12
It happened to me every time, so restarting it wasn't an option
If found out about, and successfully used two different ways to fix the problem. One was the startup script (not that hard) and the other is absurdly easy.
In System -> Preferences -> Sessions, choose the "Startup Programs" tab, and click new. In name, type in avant or whatever you want I suppose. In Command type: 

> sleep 10 && avant-window navigator

(I used a 10 sec delay to be on the safe side. Since your problem occurs less frequently you could probably cut that down)

If you haven't added avant to your list of startup programs and it has been starting up automatically you might run into a little problem, namely, you might get two avants starting up. The first one with the title bar as usual, and a few seconds later the one that you added to the startup programs, without a title bar (at least, thats what happened to me :-s) 
After some trial error this is what fixed it permanently. Basically, the old avant was saved in the session, so I closed avant (both of them), I went to the "Current Session" tab, removed avant-window-navigator from there, went to "Session Options" tab and saved the session. Before you save the session, you'd probably want to close anything else (like open windows etc) that you don't on startup. After that avant started up perfectly for me :) But, since your problem occurs less often, you may decide not to go through the trouble.

---

### Post by PaulFXH on 2007-06-12
Thanks for the detail.
That *sleep 10* thing looks interesting and I'll try that if and when this problem happens again. BTW, I do have AWN in my start-up sessions.

---

