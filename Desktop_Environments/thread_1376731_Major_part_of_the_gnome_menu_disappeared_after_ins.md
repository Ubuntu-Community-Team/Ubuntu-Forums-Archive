---
title: "Major part of the gnome menu disappeared after installing extra language packs."
date: 2010-01-09
forum: Desktop Environments
---

### Post by Jarige on 2010-01-09
I've got a problem here. I recently installed the Dutch language pack as I'm Dutch and wanted to see whether they were worth installing. But after a re-login, half of the menu has disappeared!
This appears on Ubuntu Netbook Remix (this is a netbook) but I changed the Netbook Remix menu to the 'Main Gnome menu' which is the little Ubuntu logo.
The problem is, that when I click that logo, none of the program categories appear. It only shows 'Places' and 'System'. 'Places' looks perfectly fine. System however, only shows 'Help and Support', 'About GNOME' and 'About Ubuntu'. So there's no way of going to 'Administration' or that other menu whom I forgot the name.
When I right click the menu, and click 'Edit Menus' nothing happens. When I add a new menu (including the 'Custom menu bar') the same happens to that menu.
I'm really happy that I made a shortcut to Google Chrome on my panel, I wouldn't be able to get help without it :P
Well, is there any way how I can get my menu items back? I'd rather have the English than the Dutch version, but the ability to choose between them is even better.

---

### Post by Jarige on 2010-01-09
I tried to add a screenshot to make it more clear, but I do not seem to be able to do so. When I press the PrtSc button on my keyboard when out of the menu it will show the normal 'Save Screenshot' screen. When inside the menu it won't.
And as I'm not able of starting any program but Firefox, Tomboy, Chrome and Gnome System Monitor there's not really any way of making a screenie. Please don't ask me to do so :)

Edit: I do have a screenshot suddenly. It just popped up in my face after sending this reply. I'll add it in the next reply, I can't seem to find an option to upload here.

---

### Post by Jarige on 2010-01-09
The screenshot.

---

### Post by sanderd17 on 2010-01-09
Do you know a way to start a command? in regular ubuntu its alt+f2 but I don't know this for a netbook. When you found this, you can maybe try to edit your menu with the menu editor: execute
```
alacarte
```

ps: als je spellingsfouten bij mij ziet mag je dat ook zeggen hoor :p

---

### Post by Jarige on 2010-01-09
I can start it using ALT-2, it won't pop up and it doesn´t show an error. When I press ALT-CTRL-1 and type in the command it shows a whole lot of output and terminates. This is the output (I had to manually type it all over, so this is only the error part):

```

xml.parsers.expast.ExpatError:no element found:line 1,column 0
name@name-netbook:~$[6901.213199]ath5k phy0: noise floor calibration timeout (2442MHz)

```

---

### Post by efflandt on 2010-01-09
If you **right click** on the Ubuntu symbol, can you go to **Edit Menus**, and then does **Revert** button bring the menus back?

Somehow some of my menus disappeared including Applications > Accessories and System > Preferences, but Revert button in the Menu Editor brought them back.

---

### Post by Jarige on 2010-01-10
When I click 'Edit menu' nothing happens at all... Nothing pops up...

---

### Post by sanderd17 on 2010-01-10
maybe it's not installed?
try ```
sudo apt-get install alacarte
``` if you can get into a terminal mode. 
(the gnome terminal command is gnome-terminal)

---

### Post by Jarige on 2010-01-10
Thanks for your reply. Alacarte is installed and newest version.
Thanks for the gnome-terminal command, I didn't know that one :)
I'll add it to the panel, so I'll be able to execute command there instead of another tty :)

---

### Post by sanderd17 on 2010-01-10
I found at the fedora forums where the information for the menu is kept. 
[http://fedoraforum.org/forum/showthread.php?t=13429]("http://fedoraforum.org/forum/showthread.php?t=13429")

Can you go into a terminal mode and check if the result of
```
ls /usr/share/applications
```
Is a lot of .desktop files and a few directories?

---

### Post by Jarige on 2010-01-10
Well the output is a whole lot of .desktop files indeed, and it seems none of them is gone missing, and there's a few  file that aren't .destktop files: defaults.list, screensaver and mimeinfo.cache.
Thanks for your research, I'm not new to Ubuntu, but this problem is new to me.

---

### Post by sanderd17 on 2010-01-10
I should have been smarter and searched for the error in the first place. can you try tis one?
> **RomeReactor said:**
> Hi. You could try the solution [posted here]("http://www.oddmint.com/blog/2008/05/24/how-to-reset-the-applications-menu-in-gnome/"); basically, move or rename the **applications.menu** and **settings.menu** files:
```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.backup
```
and:
```
mv ~/.config/menus/settings.menu ~/.config/menus/settings.menu.backup
```
Then log out, log back in, and see if that fixes it.

If, for any reason, you want to revert these changes, you can restore the backups you just made:
```
mv ~/.config/menus/applications.menu.backup ~/.config/menus/applications.menu
```
and:
```
mv ~/.config/menus/settings.menu.backup ~/.config/menus/settings.menu
```
found this here [http://ubuntuforums.org/showthread.php?t=856999]("http://ubuntuforums.org/showthread.php?t=856999")

---

### Post by Jarige on 2010-01-10
Thank you very much, this worked flawlessly :D
So what it did was create a new default menu because the old file was removed? Thank you again :)
If you could give me a command to remove the backups (I don't need them anymore I guess) I'd be very happy :)

Thanks again for your research, I'm most gratefull, even more because I know now that I could have found it out myself with some research.

---

### Post by sanderd17 on 2010-01-10
```
rm ~/.config/menus/applications.menu.backup
rm ~/.config/menus/settings.menu.backup
```
this will remove it.

BTW if you want to view hidden directories: press ctrl+h in nautilus.

---

### Post by Jarige on 2010-01-10
Thank you, I will mark this topic solved.
Thanks again :D

---

### Post by sanderd17 on 2010-01-10
always happy to help someone :p

---

