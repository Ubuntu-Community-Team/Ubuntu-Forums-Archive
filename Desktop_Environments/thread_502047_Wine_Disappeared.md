---
title: "Wine Disappeared"
date: 2007-07-16
forum: Desktop Environments
---

### Post by drhiii on 2007-07-16
Have searched and not found an answer yet.

Wine has disappeared from the Applications/System Tools menu.  I have another Ubuntu machine running and I have tried to compare setups.  It is available and viewable in Machine B.  But it has disappeared from Machine A, though it shows it is installing via Synaptic.  I tried completely uninstalling then reinstalling, but still no menu.

Thoughts anyone?  Running Ubuntu and Gnome.  Nothing fancy on Machine A.

tx

---

### Post by kerry_s on 2007-07-16
Why would you need it in the menu, you can't launch it by itself. It's launched when you click on the windows *.exe program. Do you mean the application you run in wine disappeared? If so just right click the menu icon and use the editor to manually put it where you want or find the application *.exe and drag it to your desktop to create a shortcut.

---

### Post by krazyenglishman on 2007-07-16
i have the same proble,

---

### Post by VitaminBB on 2007-11-11
Ya, wine disappeared from the menu here too and its not listed under "Main Menu" under "System" > "Preferences" ...

I tried uninstalling it and reinstalling it, wine exists if I type "winefile" in terminal but its disappeared from the menu ...

---

### Post by TadH on 2007-11-11
> **kerry_s said:**
> Why would you need it in the menu, you can't launch it by itself. It's launched when you click on the windows *.exe program. Do you mean the application you run in wine disappeared? If so just right click the menu icon and use the editor to manually put it where you want or find the application *.exe and drag it to your desktop to create a shortcut.
You are wrong, you can launch it via the icon

I am sorry I do not have an answer for you.

---

### Post by Darkade on 2007-11-18
Hello, I have the same problem just for me it happened after uninstalling wine. Couple weeks after unstalling it i tried to install it again it wouldn't appear in the menu.

---

### Post by Darkade on 2007-11-18
Hey I got it solved and decided to post how because lots of people seem to have the same problem.

0)You should have wine installed even though you can't see the menu
1) open your ~/.config/menus/applications.menu file
2) do a search for "wine" 
3) you'll notice that every entry that has to do with wine has a </deleted> tag, erase that tag
4) now save the file
You should now have wine menu back in your menu bar, I also changed the location of the applications-merged (It had wine related entries in it) folder but I'm not sure that has anything to do.

I got the Idea from here [http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/4de2f6c56102be46/c99a81771b0fb164?lnk=gst&q=wine+menu#c99a81771b0fb164)
thanks to the wine community and I hope this works for all of you

---

### Post by dannosenno on 2008-01-02
You will only be able to see Wine in the menu, if you have an application that can be opened by wine

---

### Post by jivixfromwc3 on 2008-02-24
Here's my case:
(Gutsy Gibbon 7.10)
When I first installed Wine, everything worked perfectly. I even got it to play Warcraft III. However, while I was experimenting with programs, I installed Super Converter. It said it didn't install properly and would exit the program. Alright, I thought I'd just run the uninstaller. Wow, didn't work. Yep, the installer was corrupted. So what did I do? I deleted the folder. But now the menu entries were stuck there, even system->preferences->main menu wouldn't delete them for some reason. I did read the above posts, and I cannot find any directory ~/.config/menus/applications.menu. However, I did find a file with root access only that did display menu items, but it was called menustructure.xml. I've only been using Linux for 2 days now and I am pretty much stumped as to how to fix it. And, yes, I've tried reinstalling. Now the Wine menu doesn't even appear under Applications. I want to get that back, at least.

---

### Post by jivixfromwc3 on 2008-02-24
Sorry, I am a noob. I forgot you could press control-h to see hidden files and so swept right past the .config folder. Ha I got it back now this was really helpful!

---

### Post by m0ns00n on 2008-04-29
I tried this, but I don't have an applications.menu in ~/.config/menus, only applications-merged with a dummy in it.

My wine menu disappeared this login, and I have no idea why. I didn't uninstall it that's for sure.

---

### Post by perelin on 2008-05-20
Thx! Darkades solution worked for me :)

---

