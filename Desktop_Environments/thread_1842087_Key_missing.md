---
title: "Key missing"
date: 2011-09-10
forum: Desktop Environments
---

### Post by Catlike on 2011-09-10
My launcher has never showed up since loading 11.04. In following kindly advice, I used the terminal to launch gconf-editor, and then went to 

/desktop/gnome/session/required_components_list/ Panel

However, the "required_components_list" folder in my Configuration Editor is named "required_components"  and in it is only one item -- something called "windowmanager".

Do I need to download a "Panel" folder? If so, how/where do I do so?

Thank you.

---

### Post by Krytarik on 2011-09-10
Since Natty 11.04, those Gconf keys aren't used anymore, the session settings are instead set by the session options. So, if you are talking about the Unity Launcher, it should show up if you choose the session option "Ubuntu", but there is a wide range of possible causes for it not showing up. Please see this guide for troubleshooting in that regard:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

If that doesn't already fix your issue, or if you are instead actually meaning Gnome Panel, for which the mentioned Gconf key was for, please post more details.

Greetings.

---

### Post by Catlike on 2011-09-12
Thank you Krytarik for your kind help. Unfortunately, after following all the applicable steps in the tuxgarage tutorial, I still have no launcher on my desktop. Now, by "launcher", I mean the column of icons (like buttons) on the left side of the screen; one user said this is called the "Unity bar". 
It seems odd to me that when I updated my laptop from Meerkat to Narwhal, the launcher showed up of its own accord (I did nothing "extra" or "special", so far as i recall); but not so when I did the same with my desktop computer.

---

### Post by Krytarik on 2011-09-12
Check if your current video card/driver setup is capable - or at least considered capable - to run Unity:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Also, do you see at least the top panel, as you didn't mention those at all so far?

---

