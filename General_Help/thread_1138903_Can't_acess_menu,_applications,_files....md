---
title: "Can't acess menu, applications, files..."
date: 2009-04-26
forum: General Help
---

### Post by rbubamara on 2009-04-26
Hi! I'm a Windows XP I've just installed Ubuntu for the first time. I installed it along with Windows XP, and everything was going +/- OK. 
I customized my desktop, installed the applications I needed...and when I restarted the computer, after logging in, something went wrong:
The menu bar on top, instead of having the usual (the basic menu, firefox and amsn button, exit button...), was blank, only with the clock, battery and internet connection icons. The internet connection works fine, but I can't access any application, settings or files! 
When I clicked on the only shortcut I had on the desktop, for My Documents file, an error message appeared. 
The bar on the bottom, with the "litter bin" completely disappeared too. 
When I right-click on the desktop nothing happens. 

This means that right now I can't do absolutely nothing with my Ubuntu and had to go back using Windows XP... What can I do? 
Note that I'm a total Linux newbie. :(

Thank you!

---

### Post by mb_webguy on 2009-04-26
Well, everything on the Gnome panels is an applet or a launcher (i.e. shortcut), and that includes the menu.  Just right-click on the panel, select "Add to panel", and add the Menu Bar applet.  You could alternatively add the Main Menu applet, which is more like the Windows start menu.

I don't know why everything disappeared on you, but if you want to reset your panels to the default and start from scratch, open the terminal (Applications->Accessories->Terminal) and paste the command "rm -r ~/.gconf/apps/panel".  When you log out and log back in, everything will be reset to the defaults.

---

