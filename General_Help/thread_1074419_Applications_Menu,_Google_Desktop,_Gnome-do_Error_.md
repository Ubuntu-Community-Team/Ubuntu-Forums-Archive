---
title: "Applications Menu, Google Desktop, Gnome-do Error and Pidgin Error!"
date: 2009-02-19
forum: General Help
---

### Post by Schok on 2009-02-19
Help! Something weird is going on..

1. My "Applications" menu isn't showing anything. When i click on it, only a tiny box appear on the left where the drop down menu should have been.

2. Google desktop and Gnome-do was added as a startup program. Now both programs do not appear after a reboot. They don't even start manually!

3. Everytime i try to start pidgin it'll just show up a few secs then closes while trying to login to my yahoo messenger, msn and facebook accounts.

Never had any of these problems before. All i could remember was that while shutting down, there was an unknown program that was still running. It has showed up before while shutting down, so i presume it was nothing much and continued my shut down since waiting for it to finish takes forever. I hope that wasn't the problem. Didn't do any major updates today except updated my wine to .15. Any help is appreciated. Thx

---

### Post by Schok on 2009-02-19
turns out pidgin error was caused by /home being full..

---

### Post by Schok on 2009-02-19
bump..can anyone help plz?

---

### Post by mc4man on 2009-02-19
> 1. My "Applications" menu isn't showing anything.

Browse here
places -> home folder -> .config -> menus and delete the file *applications.menu*
Your applications menu will be restored.

(.config is a hidden file, if not seen, then when you open your home folder go view -> "Show Hidden Files"

Or just go Places -> Home Folder, remove what's in your location bar and paste this in and press enter
```

~/.config/menus/
```

---

### Post by Schok on 2009-02-20
it worked! cant believe its THAT easy. thank you! 
long live ubuntu

---

