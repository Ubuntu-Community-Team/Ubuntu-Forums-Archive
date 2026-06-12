---
title: "Can't open anything on second x screen"
date: 2009-05-07
forum: Desktop Environments
---

### Post by badfish69 on 2009-05-07
I used the proprietary nvidia drivers to set up a dual display. I can see my second x screen, I have all the menus for it, etc. However, when I try to use firefox, for example, it opens a firefox window on my first desktop screen. If I try to drag it over to the right, it just sends it to my other workspace. Trying to explore my computer contents or my trash has the same problem, in that it is opened on the first desktop.

---

### Post by bigbudz on 2009-05-08
There's 3 options for configuring a second display. 
1. disabled
2. Twin-View
3. Seperate X-Screen. 

You have Seperate X-Screen enabled. Try switching to twin view.  
From terminal type gksudo nvidia-settings 
or System>Admin>nVidia X Server Settings and configure your second display. 
It will spread your background image over the two screens and you can put stuff on the second screen. If you maximize a screen it will open across the two screens. 
I didn't have permission when I used the system>Admin way and couldnt save anything and had no choice but to use the terminal. 
When you have the seperate X-screen option enabled can you run firefox on your 2nd display when you have another copy of firefox running on your primary display? I can't for some reason.

---

