---
title: "Compiz at startup (reloading windows manager) plus missing panels HELP"
date: 2008-08-29
forum: Desktop Environments
---

### Post by pharadox on 2008-08-29
I managed to successfully install compiz-fusion on my dell latitude d600, and then started messing around with it to see how I could get different backgrounds on all the different screens. Somehow, I changed some setting so that compiz wouldnt autostart anymore.  I would have to reload the windows manager every time.  

I tried adding compiz --replace and emerald --replace to the startup programs, but this didn't change anything.  However, adding compiz-decorator worked!  Unfortunately, when I used this I couldn't see the gnome panel at the top.  My Avant Window Navigator did load, though.  I had a shortcut in there to load the terminal, but nothing would show on the desktop.  If I start a failsafe session, everything shows up fine, but I still have to reload the windows manager to get my desktop effects.

How can I fix it so I can have the panels and not have to reload the manager every time without having to start in failsafe mode?

---

### Post by JECHO on 2008-08-29
> **pharadox said:**
> I managed to successfully install compiz-fusion on my dell latitude d600, and then started messing around with it to see how I could get different backgrounds on all the different screens. Somehow, I changed some setting so that compiz wouldnt autostart anymore.  I would have to reload the windows manager every time.  

I tried adding compiz --replace and emerald --replace to the startup programs, but this didn't change anything.  However, adding compiz-decorator worked!  Unfortunately, when I used this I couldn't see the gnome panel at the top.  My Avant Window Navigator did load, though.  I had a shortcut in there to load the terminal, but nothing would show on the desktop.  If I start a failsafe session, everything shows up fine, but I still have to reload the windows manager to get my desktop effects.

How can I fix it so I can have the panels and not have to reload the manager every time without having to start in failsafe mode?





i believe i can help you... remove the compiz --replace and emerald --replace from the start up programs and (assuming you have emerald installed and want to use it instead of metacity) open up compiz config settings manager... make sure window decoration is enabled and click it...

then delete whatever is in the "command" input box and replace it with 
```
emerald --replace
```


logout and log back in and it should be fixed. If not, let me know whats wrong.

---

### Post by pharadox on 2008-08-30
emerald --replace was already in the command input box.  I tried replacing it again anyways, but nothing changed.  When I load in the normal mode, all I see is the background wallpaper.  the only command that works is ctrl-alt-backspace.

---

### Post by JECHO on 2008-08-31
> **pharadox said:**
> emerald --replace was already in the command input box.  I tried replacing it again anyways, but nothing changed.  When I load in the normal mode, all I see is the background wallpaper.  the only command that works is ctrl-alt-backspace.



hmm... try resetting the default value. (instead of using the emerald --replace command.

---

### Post by pharadox on 2008-09-01
what's the default value?

---

### Post by pharadox on 2008-09-09
Ok, I figured out that I can set it to the default value by clicking the broomy looking icon, but that still didn't fix anything. 

I'm at the point now where my startup programs include gnome-panel, compiz-decorater, emerald --replace and compiz --replace.  I still have to reload the windows manager everytime, but when I do everything works, and at least I have panels.


So what should I do so I don't have to reload the window manager?

---

### Post by dseybert on 2008-09-13
I'm having the same issue. Consider this a free bump.

---

### Post by EnGorDiaz on 2008-09-13
ok everyone

system>preferences>sessions

add
compiz--replace in the command
emerald--replace in the command

and also do alt f2 and the run the two command in there :)

---

### Post by dseybert on 2008-09-13
> **pharadox said:**
> I tried adding compiz --replace and emerald --replace to the startup programs, but this didn't change anything.

That was the first thing we both tried. Thank you though.

---

### Post by pharadox on 2008-10-07
hey!
thanks for bringing this back.  It's nice to know that other people have this problem too.  Any results yet?

---

### Post by boc-sixtyniner on 2008-10-08
I'm going to gratuitously bump this also... for a few weeks now I've been having the same problem & tried all the previously mentioned fixes to no avail. I can't imagine that this issue isn't fairly widespread. Or maybe it's just a couple people. I dunno. Either way, it's somewhat odd that adding "emerald --replace" to the startup script doesn't work, but alt+f2 with the same command does.

---

### Post by Karlabuzer on 2008-10-30
Can somebody help me to find "preferences" under "system"?
I havent any submenus under "system" at all...:confused:

---

### Post by hermes0710 on 2008-10-30
I suggest you delete the compiz settings from your home folder and re-configure it on your next login.

---

### Post by bluemm on 2008-11-01
i have the same issue as of tonight.  i was playing around with some menu options under System.  i think it must be the session option that caused this because i clicked on the "automatically remember...logging out" checkbox under the session options tab just to see what would happen.

is there a fix for this yet?

---

### Post by ieatfish on 2008-11-24
Same problem here.  All my settings are as have been suggested and I still have to reload every time.  Any fix yet?

edit:  I have found a fix that I like.  Install the Compiz Fusion Icon and put it in the sessions to start up at boot.  It is called fusion-icon.  Make sure you have selected compiz as your window manager.

---

