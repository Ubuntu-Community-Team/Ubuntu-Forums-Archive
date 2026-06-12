---
title: "No way to add a main menu item"
date: 2012-10-21
forum: Desktop Environments
---

### Post by stephaneeybert on 2012-10-21
Hello,

It's surprising that adding an item in the main menu is so difficult.

First, I tried to right click on the main menu to access some kind of editor but there seems not to be any, one has to find and download such an editor from the ubuntu repository.

So, I installed Alacarte and it showed up in the Accessories sub menu.

I then tried to add a menu item, one pointing to the gnome-editor, (EDITED sorry I mean gnome-terminal) but it never shows up in the menu. I tried to add it in the Accessories sub menu. I tried as my user, and later on tried also as root. I logged out and in. Nothing helped.

Also, the Others sub menu does not appear in the menu, even if it is not hidden.

I'm using Lubuntu 12.10

---

### Post by delqhi on 2012-10-21
if i'm not mistaken, your problem is adding one more list item to main menu right?

in debian gnome-desktop, there is one (hidden) debian menu that will list all the installed application , even if that application has no GUI. in ubuntu gnome-desktop, this menu is empty and i think lubuntu-desktop does not have something equivalent of that.

for me, alacarte shown up in this location:
main menu button >preferences>Main Menu 

my lubuntu is default installation. i already have gnome (sudo apt-get install gnome-desktop-environment) and only remove gdm, gnome-shell and gnome-session before installing lubuntu (sudo apt-get install lubuntu-desktop). alacarte only work to hide and unhide menu, i receive error while trying to add new menu.

---

### Post by vasa1 on 2012-10-21
> **stephaneeybert said:**
> Hello,

It's surprising that adding an item in the main menu is so difficult.

First, I tried to right click on the main menu to access some kind of editor but there seems not to be any, one has to find and download such an editor from the ubuntu repository.

So, I installed Alacarte and it showed up in the Accessories sub menu.

I then tried to add a menu item, one pointing to the gnome-editor, but it never shows up in the menu. I tried to add it in the Accessories sub menu. I tried as my user, and later on tried also as root. I logged out and in. Nothing helped.

Also, the Others sub menu does not appear in the menu, even if it is not hidden.

I'm using Lubuntu 12.10
Hi! I don't understand what you are trying to do and what your problem is.

1: do you have a pure Lubuntu 12.10 installation?
2: what do you mean by gnome-editor? Are you referring to gedit?
3: I'm not sure Alacarte works well with Lubuntu.
4: At what level in the menu do you expect to see "others"? Even I don't have it.
5: Leafpad is the default text editor in Lubuntu.

---

### Post by vasa1 on 2012-10-21
BTW, I added Geany and medit. Both can be considered to be text editors. Geany shows up automatically in "Programming" while medit shows up automatically in "Accessories".
Also, while installing software requires sudo, the rest, putting stuff in the menu, is taken care of by the system.

---

### Post by delqhi on 2012-10-21
> **vasa1 said:**
> Hi! I don't understand what you are trying to do and what your problem is.
2: what do you mean by gnome-editor? Are you referring to gedit?
3: I'm not sure Alacarte works well with Lubuntu.
4: At what level in the menu do you expect to see "others"? Even I don't have it.
5: Leafpad is the default text editor in Lubuntu.

2: agree, perhaps he want to install some kind of text editor, but it's not shown up in menu.
3: alacarte work only hide and unhide menu for me, i never uninstall gnome-desktop-environment, i got some error when try to add new menu
4: there is some kind "other" menu in gnome-desktop, there is also hiden "debian" menu (in debian, not ubuntu) that will list all installed app.
5: perhaps he need to know how to install leafpad and what is the command to start leafpad and manually add menu in lubuntu (usually required command for that app)

---

### Post by slavssn on 2012-10-21
I can offer you some tips about adding menu entries without using extra software.

[LIST=1]
[*]Press Alt+F2 (or select "run" from start menu) and type:```
gksudo pcmanfm /usr/share/applications
```
Then enter your password when asked.
[*]Open any desktop file in a text editor, here's my example of leafpad.desktop file:```
[Desktop Entry]
Name=Leafpad
Comment=Simple text editor
Comment[pl]=Prosty edytor tekstu
Exec=leafpad %f
Icon=leafpad
Terminal=false
Type=Application
MimeType=text/plain
Categories=GTK;Utility;TextEditor;
```
The attributes shown are pretty simple but I'll explain them anyway:
**Name** - name shown in start menu
**Comment** - comment shown in start menu (on hover)
**Exec** - command needed to start the program (as for leafpad, it should start just fine without the f flag)
**Icon** - you can specify any icon, e.g. Icon=/home/user/images/icon.png
As for the rest of it, I think they're clear enough. This knowledge is sufficient enough to be able to create your very own menu entries :).
[/LIST]

If you want to get rid of some menu entries, you don't even need to delete them from /usr/share/applications directory. Instead, add this handy line to .desktop files:
```
NoDisplay=true
```

---

### Post by cmcanulty on 2012-10-21
install LXDE Main Menu Editor

---

### Post by wojox on 2012-10-21
> **cmcanulty said:**
> install LXDE Main Menu Editor

+1 it makes life pretty simple. :P

---

### Post by delqhi on 2012-10-21
[http://sourceforge.net/projects/lxmed/]("http://sourceforge.net/projects/lxmed/")

---

### Post by stephaneeybert on 2012-10-25
Me to, Alacarte shows up the same "Main Menu" entry in the "Accessories" menu.

---

### Post by stephaneeybert on 2012-10-25
1: do you have a pure Lubuntu 12.10 installation?
Yes, a fresh install.

2: what do you mean by gnome-editor? Are you referring to gedit?
Sorry, I meant the gnome-terminal in fact.

3: I'm not sure Alacarte works well with Lubuntu.
Indeed, it does not seem to.

4: At what level in the menu do you expect to see "others"? Even I don't have it.
I don't have an "Others" menu either. I thought there was supposed to be one, but maybe not.

5: Leafpad is the default text editor in Lubuntu.
I'm happy with vim.

---

### Post by stephaneeybert on 2012-10-25
My /usr/share/applications/gnome-terminal.desktop file contains:

[Desktop Entry]
Name=Gnome Terminal
Comment=Use the Gnome Terminal on the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.6.0
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Keywords=Run;
Actions=New
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
OnlyShowIn=Unity

But no such menu entry is being displayed in any menu.

By the way, sorry for my late reply to your posts you all, but I don't get email notifications on new posts.

---

### Post by stephaneeybert on 2012-10-25
My Lubuntu 12.10 Software Center does not have a "LXDE Main Menu Editor" nor a "LXMenuEditor". It has the Edubuntu one which I have not yet tried.

---

### Post by stephaneeybert on 2012-10-25
In the /usr/share/applications/gnome-terminal.desktop file I commented out the line

#OnlyShowIn=GNOME;Unity;

and the menu entry then showed up fine in the "Accessories" menu.

---

### Post by vasa1 on 2012-10-25
> **stephaneeybert said:**
> 1: do you have a pure Lubuntu 12.10 installation?
Yes, a fresh install.
....
So I asked about a "pure" Lubuntu and you mentioned a "fresh" one. Either way, **gnome-terminal** isn't there by default. No wonder you had problems. Anyway, people looking to mix-n-match may be helped by your solution.

---

### Post by stephaneeybert on 2012-10-25
Sorry if I misunderstood what you meant with "pure".

Yes, indeed, I had installed gnome-terminal after the Linux installation.

---

### Post by cmcanulty on 2012-10-25
get the menu editor here
[http://lxmed.sourceforge.net/download.html]("http://lxmed.sourceforge.net/download.html")
or here
[http://opendesktop.org/content/show.php?content=138298]("http://opendesktop.org/content/show.php?content=138298")

---

