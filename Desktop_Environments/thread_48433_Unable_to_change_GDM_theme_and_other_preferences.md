---
title: "Unable to change GDM theme and other preferences"
date: 2005-07-12
forum: Desktop Environments
---

### Post by awtomlinson on 2005-07-12
I am unable to change my GDM theme even though my desired theme is present in the theme selector.  I have deleted all of the built in Ubuntu themes, other than the Human theme, which cannot be deleted.  If I select my desired theme, it does not change.  Rebooting or logging out does not help.  I have also tried this while logged in as root, to no avail.  

On another note, I am also unable to change the default Open With application for file types.  The same thing occurs as with the GDM theme.  My desired application is listed, but I am unable to fill in the radio button.  I have also tried this while logged in as root, to no avail.  Is this a GNOME 2.10 bug?  All of the above was possible with Ubuntu 4.10.

---

### Post by frodon on 2005-07-12
Generally when you install a new theme you have to select the theme and click on details button to select it, some themes are only in control field or windows field. You have also icons themes which will sometime not appear in general menu.

---

### Post by varunus on 2005-07-12
By GDM theme, do you mean GTK theme?  that's the way all your windows look.  GDM theme is the login manager theme...

If you do mean GTK theme, sounds like you are missing some theme engines.  You can get them in Synaptic by getting the gtk2-engine-whatever.  Most themes require some engines, such as the smooth engine, the clearlooks engine, and the pixmap engine.

Good luck.

---

### Post by Kingedgar on 2005-07-12
Are you in System -> Administration -> Login Screen Setup to change your GDM theme?

---

### Post by awtomlinson on 2005-07-12
yes, i am going through System -> Administration -> Login Screen Setup.  any thoughts on the Open With application defaults?

---

### Post by awtomlinson on 2005-07-14
Can anyone help with these two issues?  Does anyone else have a similar issue?

---

### Post by awtomlinson on 2005-07-14
anyone????

---

### Post by gnaunited on 2006-12-14
I am having the same problem. I installed the extra themes for gdm from synaptic but it will not let me select it.

---

### Post by gnaunited on 2006-12-14
Actually click on the circle to select it, not just the theme itself.

---

### Post by mochiko on 2008-06-05
I'm having the same problem. The installed theme shows up in the theme window(in the Login Window)

Selecting the circle and not just clicking the theme does not help. 
I deleted the human themed login, which kept showing up even though i selected a different one. 

After i deleted it, i logged out and came back. This window popped up saying the Human Theme could not be loaded because it could not be found under usr/share/gdm/themes

so now, everytime i log in, that window pops up, and THEN a theme that i did not select is shown! 

Is there any way to change default gdm settings?

---

