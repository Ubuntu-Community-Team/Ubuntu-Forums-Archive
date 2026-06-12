---
title: "gconf-editor removing the gnome panel"
date: 2009-12-30
forum: Desktop Environments
---

### Post by newb85 on 2009-12-30
Whilst attempting to remove the gnome panel (to make way for a Cairo Dock) in an easily reversible fashion, I've run into a few quirks which have me baffled.  I'm probably missing something, so I'll refrain from calling any of them bugs and instead describe them here in hopes of answers from someone(s) more knowledgeable than I.

First off, here's the method CD's help recommends:
> Open gconf-editor, edit the key /desktop/gnome/session/required_components_list, and erase its content ("panel").  Restart your session : the GNOME-panel will not be started.That method did not work in its unmodified form.  The panel still persists in spite of attempts to "killall" it.  I also attempted to go down one tier in the folder list and remove the value of "panel" (gnome-panel).  I can't say why that method didn't work, either (even when I replaced the value with "__" in case of default behavior for blank values).  Then I got the brilliant idea of using gconf to force Cairo-Dock; when I replaced the value of "panel" with cairo-dock, gconf did not force CD, but it did finally stop forcing the panel.  :confused:

Also, I read somewhere that these settings should be accessible in the terminal under the folder .gconf in the home directory.  It appears that, while this is the case, folders shown in gconf-editor do not exist in the .gconf folder unless something within them has been changed from its default value.  For example, in my case, the folders existed as far down as .gconf/desktop/gnome, but the folder "session" didn't exist until *after* I used gconf-editor to change the value of "panel" to cairo-dock.  I suppose this behavior makes sense, but it did have me frustrated for some time.

Thirdly, I've heard several people quip that Ubuntu is superior to Windows because you don't have to reboot when changes are made.  Isn't there a way to make GNOME reload its configuration without completely rebooting?

Input would be appreciated.  Thanks!

---

### Post by arubislander on 2009-12-30
> **newb85 said:**
> Thirdly, I've heard several people quip that Ubuntu is superior to Windows because you don't have to reboot when changes are made.

Now, wouldn't that be a silly reason for finding Linux in general, and Ubuntu in particular, superior to Windows?

> **newb85 said:**
> Isn't there a way to make GNOME reload its configuration without completely rebooting?

Sure, you could just log off and then back on... No need to completely reboot.

---

### Post by howefield on 2009-12-30
> **newb85 said:**
> The panel still persists in spite of attempts to "killall" it.

Would right clicking the panel and selecting "Delete this Panel" be out of the question ?

---

### Post by fabounet on 2009-12-30
I confirm that on some machines, removing the content of the key /desktop/gnome/session/required_components_list/panel is not enough, and you need to write "cairo-dock" instead of "gnome-panel"
This sounds like a bug in Gnome, because it is not always needed, and also because it doesn't launch the dock on startup.

I'll update the help with this info.

---

### Post by newb85 on 2009-12-30
> **howefield said:**
> Would right clicking the panel and selecting "Delete this Panel" be out of the question ?

The "Delete this Panel" option is always ghosted out on the last remaining panel.  Since the only way to add a panel is by right-clicking on an existing panel, I guess the developers were trying to protect the clumsy user from accidentally deleting all his/her panels and being unable to get them back.  (Yes, there are probably config files that could be modified in such a case to get the panels back.)

---

### Post by newb85 on 2009-12-30
> **fabounet said:**
> I confirm that on some machines, removing the content of the key /desktop/gnome/session/required_components_list/panel is not enough, and you need to write "cairo-dock" instead of "gnome-panel"
This sounds like a bug in Gnome, because it is not always needed, and also because it doesn't launch the dock on startup.

I'll update the help with this info.

Thanks!  

Note also, that once CD is running with "cairo-dock" as the panel key, if you close CD, gnome won't restart it.

---

### Post by howefield on 2009-12-30
> **newb85 said:**
> The "Delete this Panel" option is always ghosted out on the last remaining panel.  Since the only way to add a panel is by right-clicking on an existing panel, I guess the developers were trying to protect the clumsy user from accidentally deleting all his/her panels and being unable to get them back.  (Yes, there are probably config files that could be modified in such a case to get the panels back.)

You are quite correct, I thought it was the bottom panel you were removing whilst leaving the top panel. Obviously not the case :)

---

### Post by Albert Net on 2010-01-09
What if I use gnome-do? 

I tried to write "gnome-do" and it did not work.

Any suggestion?

---

### Post by zeroseven0183 on 2010-01-15
> **Albert Net said:**
> What if I use gnome-do? 

I tried to write "gnome-do" and it did not work.

Any suggestion?

I've been thinking of doing this also but same results as yours.
What I did was tick the option to start Gnome Do on login.

---

