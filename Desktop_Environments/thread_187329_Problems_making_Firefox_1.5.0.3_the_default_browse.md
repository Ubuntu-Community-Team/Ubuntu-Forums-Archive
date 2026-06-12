---
title: "Problems making Firefox 1.5.0.3 the default browser"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mwneal on 2006-06-02
I am currently using the latest version of Firefox downloaded from Mozilla's website, and it doesn't seem to want to become the default browser. No dialog appears when starting FF up (as it should), and even when I go to Edit > Preferences and click the button to have it check, it doesn't seem to be doing anything. Any help?

---

### Post by NewWithoutClue on 2006-06-02
Did you remove the older version of Firefox? If not, this could be the cause. Try removing the older version and then starting FF back up. If this does not help, remove the newer version and then reinstall it.

On a side note, Gnome allows you to set the default Web Browser via a handy configuration tool located in "Desktop->Preferences->Preferred Apllications". This can also be set via the Gconf tool, but that's basically over-kill in most situations.

Regards,
Paul.

---

### Post by aysiu on 2006-06-02
How did you "install" this new version (by the way, we're now at 1.5.0.4)? That may have something to do with it.

I would highly recommend [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

---

### Post by cgjones on 2006-06-02
[QUOTE=aysiu]How did you "install" this new version (by the way, we're now at 1.5.0.4)? That may have something to do with it.

I would highly recommend [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).[/QUOTE]

What's up with that URL? pykeylogger?

---

### Post by aysiu on 2006-06-02
[QUOTE=cgjones]What's up with that URL? pykeylogger?[/QUOTE] It's owned by the forum member *nanotube*, who has worked really hard to make that script work extremely well.

From [the main page](http://pykeylogger.sourceforge.net/): > PyKeylogger is a simple keylogger written in the python programming language, and is available under the terms of the GNU General Public License. I threw it together one day after not being able to find a simple and trustworthy keylogger for windows, and it sort of snowballed from there. It is currently only available for the Windows OS, due to its using Windows-specific APIs.

It is primarily designed for personal backup purposes, rather than stealth keylogging. Thus, it does not make explicit attempts to hide its presence from the operating system or the user. That said, the only way it is visible is that the process name shows up in the task list, so it is not immediately apparent that there is a keylogger on the system. However, since it also makes periodic writes to disk, and since it openly hooks well-known windows APIs (SetWindowsHookEx), any keylogger detector worth its salt will be able to sniff it out. So basically, it doesn't exactly advertise itself, but doesn't hide itself either. 

---

### Post by cgjones on 2006-06-02
Cool. I got a little leery when I saw the URL.

---

