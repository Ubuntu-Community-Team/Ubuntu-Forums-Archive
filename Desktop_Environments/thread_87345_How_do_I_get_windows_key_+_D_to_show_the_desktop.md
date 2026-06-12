---
title: "How do I get windows key + D to show the desktop?"
date: 2005-11-07
forum: Desktop Environments
---

### Post by aaronshaf on 2005-11-07
How do I get windows key + D to show the desktop?

---

### Post by aysiu on 2005-11-07
Use KDE.

---

### Post by aaronshaf on 2005-11-07
Is there no way in Gnome?

---

### Post by aysiu on 2005-11-07
There is a way, but I don't know how to do it. It has something to do with changing the way the Win key behaves. It's either in System > Preferences or Applications > System Tools > Configuration Editor somewhere.

---

### Post by SickTwist on 2005-11-07
System --> Preferences --> Keyboard Shortcuts

The last item in the Window Management section is "Hide all windows and focus desktop", click on that and press the desired key combination to set it.

---

### Post by aaronshaf on 2005-11-07
Thanks!!!

---

### Post by stubby on 2005-11-08
If you just want the show desktop function it is

CTRL + ALT + D

You get used to it after a while.

---

### Post by divel on 2005-11-10
I'm a sucker for windows shortcuts (I must admit :X), so there are some of the keyboard shortcuts I would really like to use, including the previously mentioned win+m to show the desktop.

Fx: 
win+r to open a console
win+e to open the home folder/nautilus

Anyone?

Thanks

---

### Post by kxs on 2005-11-11
I know 2 ways:
-run gconf-editor
-go to apps-metacity-global_keybindings
-on run_command_1 for example add <Mod4>e
-go to keybindings_commands and on command_1 add nautilus

2nd way (you can change few shortcuts with this):
-go to System-Preferences-Keyboard Shortcuts
-find what you want, for example Show Desktop or Run Terminal and simply change a shortcut ;)

---

### Post by kinson on 2006-11-30
> **SickTwist said:**
> System --> Preferences --> Keyboard Shortcuts

The last item in the Window Management section is "Hide all windows and focus desktop", click on that and press the desired key combination to set it.

I can't seem to get this working with Windowskey+D :(

I hit "windowskey" and it assigns just that key to the shortcut(show desktop), and when I hit "D", it takes me to the top of the list "desktop"

I held the windows key and hit D :(

Btw, is there any way to set a shortcut to focus on the current open instance of the terminal?

Cheers,
Kinson :)

---

### Post by cookfromfrozen on 2006-12-04
> **kinson said:**
> I can't seem to get this working with Windowskey+D :(
Paste this into a terminal and press enter:
> gconftool-2 -t str --set /apps/metacity/global_keybindings/show_desktop "<Mod4>d"

---

### Post by kinson on 2006-12-04
> **cookfromfrozen said:**
> Paste this into a terminal and press enter:

Cool, thanks man :)

Its working now :)

Cheers,
Kinson

---

### Post by krazyman on 2007-02-19
Hello,

I can get my windows key - D combo to work, but I can't seem to get windows-L to work to lock the screen. The keyboard editor lets me enter the combo, but it doesn't do anything when I press it. I have set my keyb prefs to 'Super is mapped to the Win-keys (default)', which produces <Mod4><Hyper>l when I press Win-L.

Does anyone have any ideas what's happening?

---

### Post by jazzgossen on 2007-03-21
> **krazyman said:**
> I can get my windows key - D combo to work, but I can't seem to get windows-L to work to lock the screen. The keyboard editor lets me enter the combo, but it doesn't do anything when I press it. I have set my keyb prefs to 'Super is mapped to the Win-keys (default)', which produces <Mod4><Hyper>l when I press Win-L.

Does anyone have any ideas what's happening?

I have the same problem. Win+d works for showing the desktop, and Win+t works for starting a terminal. However, Win+l (lock screen) Win+w (start web browser) and a few more Win+X combinations do nothing. 

I have the super key mapped to the win key, and keyboard shortcut preferences dialog says <Mod4>+W etc.

---

### Post by wolterh on 2008-02-04
I know how to do it. Even though, I'm no expert. These guys should know this.
-type gconf-editor in terminal
-go to /apps/metacity/global_keybindings/
-search for an entry called show_desktop
-right-click and select edit key
-type in '<Super>D'
-search for an entry called run_command_terminal
-repeat steps above but type '<Super>R'

I don't know how to do the home folder thing.
Thank me if it works please !

---

### Post by luke16 on 2008-03-15
>  			 		 		 		 		I know how to do it. Even though, I'm no expert. These guys should know this.
-type gconf-editor in terminal
-go to /apps/metacity/global_keybindings/
-search for an entry called show_desktop
-right-click and select edit key
-type in '<Super>D'
-search for an entry called run_command_terminal
-repeat steps above but type '<Super>R'

I don't know how to do the home folder thing.
Thank me if it works please !
Show desktop and run terminal already work for me. How do you do lock screen? There isn't an option for that in gconf-editor

---

### Post by Xolamee on 2008-07-15
When you try to use System>Preferences>Keyboard Shortcuts to set the "Hide all windows and focus the desktop" shortcut to Win+D (or Super+D for us ubuntu folks) it just sets it to Super, and ignores the D part. The best fix I've seen that works the most is..

Go to the Terminal (Applications>Accessories>Terminal)
Type gconf-editor
The editor will pop up.
Double-click "apps"
Then double-click "metacity"
Click "global_keybindings"
Find "show_desktop" in the panel on the right
Change the value to "<Super>d"

---

