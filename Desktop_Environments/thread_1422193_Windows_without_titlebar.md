---
title: "Windows without titlebar"
date: 2010-03-05
forum: Desktop Environments
---

### Post by kristianjohann on 2010-03-05
Salvete!

I have the following problem: I have installed Unbuntu 9.10 on my machine (Medion Akoya E1210) and set up two user accounts. User account A works without problems, user account B not. If I log in to B, then I'm able to start programs, but the windows of the programs are without titlebar (that is the bar with: Minimize/Maximize/Move/Allways on top/Close-functions, Title, Minimize/Maximize/Close-functions). If I set the visual effects to normal (left click on the desktop/Change Background/Visual effects/Normal), then the windows are shown normaly, that is amongst others with titlebar. If I log out of B and log in again, then the Visual effects are set to None and I have to set it to Normal again.
My question: How can I save the Visual effects state Normal between log out and log in, etc.?

Many thanks and kind regards, Christian

---

### Post by Yanno on 2010-03-05
> **kristianjohann said:**
> Salvete!

I have the following problem: I have installed Unbuntu 9.10 on my machine (Medion Akoya E1210) and set up two user accounts. User account A works without problems, user account B not. If I log in to B, then I'm able to start programs, but the windows of the programs are without titlebar (that is the bar with: Minimize/Maximize/Move/Allways on top/Close-functions, Title, Minimize/Maximize/Close-functions). If I set the visual effects to normal (left click on the desktop/Change Background/Visual effects/Normal), then the windows are shown normaly, that is amongst others with titlebar. If I log out of B and log in again, then the Visual effects are set to None and I have to set it to Normal again.
My question: How can I save the Visual effects state Normal between log out and log in, etc.?

Many thanks and kind regards, Christian

Hi!
Go to Compiz and choose "Windows decoration".See whether there's something wrong with the command.If there is,try set it  to default!

---

### Post by kristianjohann on 2010-03-05
Salve Yanno!

That's the problem - better: was the problem. Compiz didn't start with the session. So I add compiz to the startup applications and now windows are displayed normaly.

Many thanks and an extra bean for you... Christian

---

