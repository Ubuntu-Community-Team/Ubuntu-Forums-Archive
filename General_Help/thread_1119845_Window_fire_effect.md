---
title: "Window fire effect"
date: 2009-04-08
forum: General Help
---

### Post by Talynz on 2009-04-08
How do I make it where when I close a window, the window gets set on fire. It burns up. I've seen it on videos and i really would like to do it, but im a noob and i don't know how. Please help! 
And i have Ubuntu 8.1

---

### Post by Vaphell on 2009-04-08
run compiz properties app (probably can be found in Preferences menu: Advanced Desktop Effect Settings or use ccsm in terminal). I use 8.04 so can't say if there are differences compared to 8.10

go to Animations, you should find a lot of tabs there - with settings for various events (open window, close window, minimize, etc)
Set Flame/Fire (or whatever that effect is called) to be used on the 'close window' tab. As you can see, you are even able to define different behavior for different window types.

I haven't produced exact steps to follow, but i think you'll figure it out :)

---

### Post by The Cog on 2009-04-08
You need to install package compizconfig-settings-manager. This is the command to do that:
**sudo aptitude install compizconfig-settings-manager**

afer which you will find the menu System->Preferences->Advanced Desktop Effect Settings. It's somewhere in there, along with lots of other options.

---

