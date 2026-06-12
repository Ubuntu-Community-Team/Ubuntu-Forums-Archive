---
title: "Cairo Dock icon for running applications"
date: 2009-01-29
forum: General Help
---

### Post by exziton on 2009-01-29
Hi! I have the problem that my Cairo Dock is not showing some icons for current applications. The dock shows the correct icon for the launcher, but when the application is running, there only appears a big question mark on the right side of the dock. It only happens to applications where I had to install a manual launcher. Does anybody know how to solve this? Thank you...

---

### Post by fabounet on 2009-01-29
normally you should add launcher by drag and drop from the Applications Menu
because the menu contains some information that will be used by the dock, like the class of the appli.
if you create your launcher manually, you may have to fill these values too.

---

### Post by exziton on 2009-01-30
Thank you for the answer. I added the application to the application menu in System > Preferences > Main Menu and added it to the Dock by drag&drop. It shows the correct icon in the application menu, but it is still not showing the correct icon in the running processes subdock. Now it is showing the Java icon, I guess thats because the application is running under Java. Does anybody perhaps know how I can change it so that it shows the correct icon in the running processes subdock? The programm ist startet by pointing to the following run script:[HTML]java -Xmx1500m -jar ~/imagej/ImageJ/ij.jar -ijpath ~/imagej/ImageJ[/HTML]

---

### Post by fabounet on 2009-01-30
I think this is normal since the class is the same
this app is seen as a java instance, and then takes the java icon.
is the icon in the gnome-panel different ?
what you can try is editing the config of your launcher, and in Extra parameters check the box about the X icons

---

### Post by exziton on 2009-01-30
Well, the launcher icon itself is correct, only the icon for the running process is wrong. The gnome panel is not showing me any icon for a running process, or does it? Checking the "Overwrite X icons with the launchers one" option in the Dock configuration does unfortunately not change anything (I alraedy tried this before). May you or anyone else perhaps have another idea?

---

### Post by Alterios on 2009-04-29
I had the same problem in 9.04 and this is how I fixed it.\\:D/ In [COLOR="Blue"]~/.config/cairo-dock/current_theme[/COLOR] I opened the [COLOR="Blue"]cairo-dock.conf[/COLOR] and found my problem deep in it's well documented bowels. There is a section that reads [COLOR="Red"]#D+99 List of icons themes or directories :
#{Directories or themes where to search icons. Put some directories where you have icons you wish to see in the dock, or put some theme's name you've installed on your system. (the order is taken into account during the research). The key word _LocalTheme_ represents the directory ~/.config/cairo-dock/current_theme/icons}/
default icon directory=~/.cairo-dock/current_theme/icons/[/COLOR].
This was what the theme I installed created by default. In the last line it is looking for [COLOR="Red"]~/.cairo-dock[/COLOR] which doesnt exist. because it cant find that folder it defaults to the basic system icons for any running window. The simple way to fix it is to change [COLOR="Red"]default icon directory=~/.cairo-dock/current_theme/icons/[/COLOR] to read [COLOR="Blue"]default icon directory=_LocalTheme_[/COLOR]. As is stated in the comments about this section of the file it will make Cairo look in the current theme folder so all you need to do is put the proper pic in that folder and make sure it is named right. I.E. firefox.png, nautilus.svg, etc. I hope this helps.[-o<

Another possible way to fix this is is to open the configuration window under "Icons" and delete everything in the icon themes box. Click the Open Button and navigate to /home/*USER NAME*/.config/cairo-dock/current_theme. If Cairo doesn't update you can close and reopen all the open windows you have to make it re-read the icon theme.

---

