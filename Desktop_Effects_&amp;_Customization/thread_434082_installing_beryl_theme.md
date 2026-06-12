---
title: "installing beryl theme"
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by Diversion on 2007-05-05
After sucesfully installing beryl on my Feisty installation (yay!)
I've downloaded a theme and am trying to install it, how do I install the theme?
If I click on the emerald icon I can't find a install theme page, 

Also a quick question:

Whenever I press SHIFT+backspace it logs me out, is there a way to change this cause I tend to press te combination now and then ;)

---

### Post by DSn0wMan on 2007-05-05
You will first need to extract the theme you downloaded from the tarball. To install a beryl theme use the emerald theme manager. Click on the improt button, and then browse to the directory where you extracted the file and select it. The file you want to import should end in .emerald

---

### Post by Campingman on 2007-05-05
You could install the Emerald theme manager it is synaptic.  
I think this should do what you need.
System>Administration>Synaptic Package Manager and do a search for Beryl and install emerald theme.

---

### Post by starcraft.man on 2007-05-05
Do you have the emerald theme manager installed?

sudo aptitude install emerald-themes

If so, and you have the manager for beryl, right click on the right gem in your tray, and select emerald theme manager. Then just push import and find the .emerald package.

Alternatively, System > Preferences > Emerald will get you to same place.

:)

---

### Post by Diversion on 2007-05-05
Emerald theme manager wasn't installed, Installed it and running a new theme happy :D

thanks!

---

### Post by starcraft.man on 2007-05-05
> **Diversion said:**
> Emerald theme manager wasn't installed, Installed it and running a new theme happy :D

thanks!

Hehe, your welcome. Sometime its the simplest things :)

---

### Post by adde on 2007-05-08
What am I doing wrong.. I have Emerald-Themes installed, but I can't change the theme.. I have downloaded a nice looking theme and extracted it. I can import it to the list of themes in Emerald theme manager, but I cannot activate it!
I can't use any of the "default" emerald themes either for that matter..

How do I change Theme?

---

### Post by starcraft.man on 2007-05-08
> **adde said:**
> What am I doing wrong.. I have Emerald-Themes installed, but I can't change the theme.. I have downloaded a nice looking theme and extracted it. I can import it to the list of themes in Emerald theme manager, but I cannot activate it!
I can't use any of the "default" emerald themes either for that matter..

How do I change Theme?


Nooooo, no extracting. You should be downloading a file that has the ending extension ".emerald" don't do anything with that (if its in a tar or bzip do extract till you get the emerald). 

Then you open the manager, right click on Red beryl, then select manager. Push the import and direct it to the .emerald file. Then just click on the file and emerald should change your theme on the fly. If it doesn't change I assume you aren't switched to the emerald theme or you aren't using Beryl.

Right click on Beryl Icon > Select WIndow Manager > Beryl

Right click on Beryl  > Select Window Decorator > Emerald

Make sure both of those are selected, else emerald won't be used as your window theme.

---

### Post by adde on 2007-05-08
> **starcraft.man said:**
> Nooooo, no extracting. You should be downloading a file that has the ending extension ".emerald" don't do anything with that (if its in a tar or bzip do extract till you get the emerald). 

Then you open the manager, right click on Red beryl, then select manager. Push the import and direct it to the .emerald file. Then just click on the file and emerald should change your theme on the fly. If it doesn't change I assume you aren't switched to the emerald theme or you aren't using Beryl.

Right click on Beryl Icon > Select WIndow Manager > Beryl

Right click on Beryl  > Select Window Decorator > Emerald

Make sure both of those are selected, else emerald won't be used as your window theme.


Aaaaah.... Beryl used the wrong window decorator. :$
Now it work perfectly.
Thanks Starcraft!

---

### Post by dannymichel on 2007-05-08
I HAVE Beryl installed. My theme decorator is checked to emerald and window manager is checked to Beryl.
I still can't select any Beryl themes.

---

### Post by Diversion on 2007-05-11
You have to reload the window decorator to apply the theme after you selected it.

---

### Post by mariavon on 2007-05-14
> How do you make sure that Beryl will load on start up cuz mine doesn´t



Nevermind I fixed it

---

### Post by Sewers on 2007-05-18
I have Emerald and Beryl installed, they both work, but Beryl does not pick up Emerald in the "Select Window Decorator". Any way to get it to get this to work? Only the GTK Window Decorator is available.

edit: Nevermind, I rebooted the machine with "emerald --replace" as a startup program.

---

### Post by jordey24 on 2008-05-12
how do i install beryl?

---

### Post by 45acp on 2008-05-12
I have the same problem. I emerald doesn't apply the theme. I can't find beryl in synaptic to install.

---

