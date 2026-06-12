---
title: "Changing Lock-dialog??"
date: 2010-02-14
forum: Desktop Environments
---

### Post by hakermania on 2010-02-14
Well......Hi!
I downloaded the Burst-lock-dialog theme from here: [http://gnome-look.org/content/show.php/Burst+Lock-Dialog+Theme?content=110992](http://gnome-look.org/content/show.php/Burst+Lock-Dialog+Theme?content=110992) ...
The instructions in order to change the default dialog theme was this:
To install, extract everything to /usr/share/gnome-screensaver/, open gconf-editor and change the value in /apps/gnome-screensaver/lock_dialog_theme to "burst".

I did this but the only I managed to do with this was to disable the "Leave message" from the default theme, although without changing anything except this.
What do I do wrong? Have I to delete some of the files that are in the /usr/share/gnome/screensaver ? If yes, these are my files in /usr/share/screensaver:
gnome-screensaver-preferences.ui  lock-dialog-default.ui


If anyone could help it would be nice!
Thx!:D

---

### Post by sot3 on 2010-04-11
So...this is marked as solved, but I don't see any solution.

How was it solved?

---

### Post by majortom117 on 2010-04-21
I have nearly the same problems with the lock dialog, I changed the value in the gconf-editor but it wasn't realised from the system.
I found a configuration file in ~/.gconf/apps/gnome-screensaver/
```
tommy@saratoga:~/.gconf/apps/gnome-screensaver$ cat %gconf.xml 
<?xml version="1.0"?>
<gconf>
    <entry name="lock_enabled" mtime="1271807232" type="bool" value="false"/>
    <entry name="lock_dialog_theme" mtime="1271358090" type="string">
        <stringvalue>**mohegan**</stringvalue>
    </entry>
    <entry name="themes" mtime="1271863625" type="list" ltype="string">
        <li type="string">
            <stringvalue>screensavers-personal-slideshow</stringvalue>
        </li>
    </entry>
    <entry name="mode" mtime="1271863625" type="string">
        <stringvalue>single</stringvalue>
    </entry>
</gconf>
```after I changed the value it worked.

ps: I also had to copy the images of the loc&#7729;-dialog theme directly in /usr/share/gnome-screensavers/

---

