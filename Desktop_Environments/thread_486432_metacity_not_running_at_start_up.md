---
title: "metacity not running at start up"
date: 2007-06-28
forum: Desktop Environments
---

### Post by dbbolton on 2007-06-28
so, i tried to install compiz fusion, and it didn't work. so i uninstalled everything and went back to my regular 'ati' driver from the 'fglrx' one.

somehow, something screwed up my gnome session, and metacity will not run at startup. also, the splash screen hangs until i click on it.

a failsafe gnome session seems to work ok, so i'm assuming that there's a start up script that i need to gid rid of.

does anyone know what's causing this problem, or what i should do to fix it?

---

### Post by alptech on 2007-06-28
hello dbbolton,
I too have the same problem. I followed the install post located elsewhere on this forum
and have encountered the same result. I tried re-installing metacity but that didn't do
anything. ](*,)

If I open a terminal and run metacity, the borders come back, but as soon as I close the
terminal the borders dissappear again. 

I have searched this forum and a couple others for an answer but have found none.
It would be greatly appreciated if anyone here could guide us in the right direction.
Thank You.

---

### Post by dbbolton on 2007-06-28
> **alptech said:**
> hello dbbolton,
I too have the same problem. I followed the install post located elsewhere on this forum
and have encountered the same result. I tried re-installing metacity but that didn't do
anything. ](*,)

If I open a terminal and run metacity, the borders come back, but as soon as I close the
terminal the borders dissappear again. 

I have searched this forum and a couple others for an answer but have found none.
It would be greatly appreciated if anyone here could guide us in the right direction.
Thank You.
i've noticed that i can get metacity to run by doing this:

open the terminal 
enter 'metacity'
press ctrl+c

then when i close the terminal, metacity still runs.

---

### Post by evilc on 2007-06-28
Don't know if this helps but if you add Metacity to your sessions startup it will start up every time you start your computer. You could also try in terminal "metacity --replace &" without the quotes.

---

### Post by kevinlyfellow on 2007-06-28
in gconf-editor (alt-f2 run gconf-editor) navigate to /desktop/gnome/applications/window_manager and change compiz to metacity

---

### Post by dbbolton on 2007-06-28
> **evilc said:**
> Don't know if this helps but if you add Metacity to your sessions startup it will start up every time you start your computer. You could also try in terminal "metacity --replace &" without the quotes.
i added "metacity" and "metacity --replace" to my startup programs, but it didn't help.

---

### Post by dbbolton on 2007-06-28
> **kevinlyfellow said:**
> in gconf-editor (alt-f2 run gconf-editor) navigate to /desktop/gnome/applications/window_manager and change compiz to metacity
i'll give this a go...

---

### Post by dbbolton on 2007-06-28
ok, that works! 

thanks guys :)

---

### Post by alptech on 2007-06-28
> **evilc said:**
> Don't know if this helps but if you add Metacity to your sessions startup it will start up every time you start your computer. You could also try in terminal "metacity --replace &" without the quotes.

I will try this when I get home, thank you for the quick replies!:D

---

### Post by alptech on 2007-06-28
okay, i tried changing the window manager value in gconf-editor to metacity but
when I log out and back in, the value goes back to ~/.gnome2/openbox.
Any ideas?

---

### Post by kevinlyfellow on 2007-06-29
> **alptech said:**
> okay, i tried changing the window manager value in gconf-editor to metacity but
when I log out and back in, the value goes back to ~/.gnome2/openbox.
Any ideas?

There are three ways that I know of getting a wm to run (ok, maybe more but for now...),  In gconf, in gnome-sessions, or in grub.  Check to make sure openbox isn't in your gnome-session.  If it isn't check to see if it is in grub (on the kernel line).

Edit, ok, I don't think it would be in grub, since gconf would be completely ignored (the value set in there will be wrong).  I'm trying to remember how gdm handles window managers, but its not coming to mind right now.  I'll get back to this in a few.

Edit2: Ok, you can look in /usr/share/xsessions and see if make sure there isn't a file there that will start gnome with openbox (if you didn't create it, its not there!).  There probably will be one for **just** openbox (which I'm assuming your not booting into),  The best suggestion I have is to run metacity and go to the gnome-sessions tool and go to the "session options" tab and save the session when metacity is running.  Make sure when you change the value in gconf you are changing the default wm not the current wm

---

### Post by alptech on 2007-06-29
> **kevinlyfellow said:**
> There are three ways that I know of getting a wm to run (ok, maybe more but for now...),  In gconf, in gnome-sessions, or in grub.  Check to make sure openbox isn't in your gnome-session.  If it isn't check to see if it is in grub (on the kernel line).

Edit, ok, I don't think it would be in grub, since gconf would be completely ignored (the value set in there will be wrong).  I'm trying to remember how gdm handles window managers, but its not coming to mind right now.  I'll get back to this in a few.

Edit2: Ok, you can look in /usr/share/xsessions and see if make sure there isn't a file there that will start gnome with openbox (if you didn't create it, its not there!).  There probably will be one for **just** openbox (which I'm assuming your not booting into),  The best suggestion I have is to run metacity and go to the gnome-sessions tool and go to the "session options" tab and save the session when metacity is running.  Make sure when you change the value in gconf you are changing the default wm not the current wm

I have done all the above. I tried saving my session with metacity running and with metacity as the default value in gconf. If i choose "failsafe gnome session" from the login screen, metacity runs fine. 
I even tried re-installing gnome, to no avail. I will work on it some more when I get home tonight, but 
I thank everyone for their help.

---

### Post by kevinlyfellow on 2007-06-29
> **alptech said:**
> I have done all the above. I tried saving my session with metacity running and with metacity as the default value in gconf. If i choose "failsafe gnome session" from the login screen, metacity runs fine. 
I even tried re-installing gnome, to no avail. I will work on it some more when I get home tonight, but 
I thank everyone for their help.

Well for a workaround, I would put metacity in grub (I think that that would override all the other methods.  Keep us informed on how it goes.

---

