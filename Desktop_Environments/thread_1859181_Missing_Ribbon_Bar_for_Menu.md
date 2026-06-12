---
title: "Missing Ribbon Bar for Menu"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2011-10-13
I switched from Gnome to XFCE yesterday. I was happily surprised when on 'launching' Gourmet Recipe Manager, the program ran perfectly. Today, the Ribbon Bar with the commands is missing. Gourmet runs, but displays no ability to enter new recipes, save new recipes, change Preferences, and all other available commands. 

What gives? If I knew XFCE better, I wouldn't have to ask this question so broadly.

---

### Post by Toz on 2011-10-13
Try pressing Alt+F2 and running the following command:
```
xfwm4 --replace
```

This will restart the window manager, which may have crashed.

---

### Post by Mark_in_Hollywood on 2011-10-14
As give, the command does not work it's magic.

Please see attached screenshots to help me clarify the problem.

---

### Post by Toz on 2011-10-14
Is xfce4-panel running? At the command prompt, run the following command:
```
ps -ef | grep xfce4-panel | grep -v grep
```

If its not running, then start it.
```
xfce4-panel
```

---

### Post by Mark_in_Hollywood on 2011-10-14
mark@Lexington-19:~$ ps -ef | grep xfce4-panel | grep -v grep

returned:

mark      1685  1666  0 08:31 ?        00:00:12 xfce4-panel --display :0.0 --sm-client-id 2e5e5b8ae-5b9e-44c8-90fa-571312f51ab7

As I have used Xfce for 48 hours I don't know what the above means, but on doing your 2nd line:

the terminal output is:

mark@Lexington-19:~$ xfce4-panel
xfce4-panel: There is already a running instance


so, I guess that's a YES.

---

### Post by Toz on 2011-10-14
Is the menu bar missing for just this program, or for all programs?

Try opening a terminal window and running gourmet from there:
```
gourmet
```

Do any error messages come up on the terminal window?

---

### Post by Mark_in_Hollywood on 2011-10-17
Is that a trick question?

Gedit has icons for file & printing operations, but no ribbon bar menu.

Google's Picass 3 - has File - Edit - View - Folder as a selectable menu.

LibreOffice has a ribbon menu.

Gourmet, run from a terminal, upon closing returned:


mark@Lexington-19:~$ gourmet
Ignoring sqlalchemy problem
Traceback (most recent call last):
  File "/usr/share/gourmet/gourmet/backends/db.py", line 224, in save
    self.db.commit()
  File "/usr/lib/python2.7/dist-packages/sqlalchemy/engine/threadlocal.py", line 78, in commit
    trans = self._connections.trans.pop(-1)
IndexError: pop from empty list

---

### Post by Toz on 2011-10-17
> **Mark_in_Hollywood said:**
> Is that a trick question?
I was wondering whether its only this program that you are experiencing this problem with or with all programs.

> Gedit has icons for file & printing operations, but no ribbon bar menu.

Google's Picass 3 - has File - Edit - View - Folder as a selectable menu.

LibreOffice has a ribbon menu.
Looks like its affecting other programs. 

Exactly how did you "switch[ed] from Gnome to XFCE"? Did you install the xubuntu-desktop package or some other method? 

What version of *buntu are you running?

It looks to me like the unity globalmenu (the one that displays the menu bars of the different applications on one main menu bar at the top of the screen - ala OSX), is still running/installed and affecting your programs.

---

### Post by Mark_in_Hollywood on 2011-10-17
> **Toz said:**
> I was wondering whether its only this program that you are experiencing this problem with or with all programs.


Looks like its affecting other programs. 

Exactly how did you "switch[ed] from Gnome to XFCE"? Did you install the xubuntu-desktop package or some other method? 

What version of *buntu are you running?

It looks to me like the unity globalmenu (the one that displays the menu bars of the different applications on one main menu bar at the top of the screen - ala OSX), is still running/installed and affecting your programs.


From:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Adding Xubuntu to an existing Ubuntu/Kubuntu
Paste in this command in the terminal:

sudo aptitude update && sudo aptitude install xubuntu-desktop

To use Xfce after you've installed it:

Log out.
Under Session, select Xfce.
Log back in again.

This install is: 

Ubuntu 11.04 - the Natty Narwhal 

32-bit - pretty much a stock install.

This is all I have done with Xfce. No mods, nothing else. Even Banshee has no ribbon bar menu in Xfce. How does that work?

---

### Post by gsmanners on 2011-10-17
That particular guide is old, written long before Unity was even a dream. Here's the guide you probably want:

[http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu](http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu)

---

### Post by Mark_in_Hollywood on 2011-10-18
> **gsmanners said:**
> That particular guide is old, written long before Unity was even a dream. Here's the guide you probably want:

[http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu](http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu)

I have looked -carefully- at the URL at askubuntu.com and it doesn't help me, as I don't use Unity. When using Gnome, I'm in Ubuntu (Classic) desktop.

When in Xfce, I have no choice as to whether the ribbon bar menus show or not. They aren't there. So, soft focus, fuzzy focus, and "ignore indicator" only makes my head spin. Sorry. I know you are helping.

When I read: "new indicator-appmenu in Maverick breaks the LyX menu" I gave up, this "Unity-Support-disabling" post maybe too out of date. 

Anybody else know why the Xfce doesn't show the standard menu at the top of the app's window?

---

### Post by Mark_in_Hollywood on 2011-10-18
Bizarrely, pressing F10 brings up the menu I most need. I don't like it this way, but rather than take more time from the Ubuntu Community, I will say 'thanks' and mark this as solved. 

PS - I don't have the other menus other than the (what would be Alt-F) and while that's a prob, I can get started and learn the mysteries of Xfce on my own time. Again, thank you for your help.

---

### Post by gsmanners on 2011-10-18
Okay, how about trying this:

```
sudo apt-get remove indicator-appmenu
```

---

