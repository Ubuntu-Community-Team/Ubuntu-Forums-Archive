---
title: "Exit button takes me back to login"
date: 2007-04-11
forum: Desktop Environments
---

### Post by nkkromhof on 2007-04-11
I've come across something that annoys me and I don't know where to look to fix it...

When I click the "Exit button" in the top right corner of the screen it automatically takes me back to the GDM Login screen, it doesn't ask me whether I want to log out, hibernate or shut down etc.

I haven't had to shut down in a while so I don't know what I changed on my system to make it change this way. 

Any clues would be helpful...

---

### Post by dbbolton on 2007-04-12
what happens if you go to System > Quit ?

---

### Post by aanderse on 2007-04-12
i think you are looking for /apps/gnome-session/options/logout_prompt in gconf

---

### Post by nkkromhof on 2007-04-13
> **aanderse said:**
> i think you are looking for /apps/gnome-session/options/logout_prompt in gconf

Yes I was apparently! Thanks for both your replies, it's much appreciated.
Makes me feel like I should have thought of searching gconf myself, another thing learned :)

I attached a screenshot for future reference if anyone stumbles on the same problem.

Edit: I feel positively silly now, the other keys in gconf made me think that this setting is controlled from System --> Preferences --> Sessions and sure enough, it has an option "Ask on logout" which is kind of cryptic but all too obvious in hindsight. I must not have been paying attention when I turned off the splash screen the other day.

---

