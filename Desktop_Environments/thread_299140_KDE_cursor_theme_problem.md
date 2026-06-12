---
title: "KDE cursor theme problem"
date: 2006-11-13
forum: Desktop Environments
---

### Post by zardoz on 2006-11-13
Hello ...
I'd like to get rid of that silly jumping little application icon at the right of the mouse pointer, when you start some application.
So I tried to install a different mouse theme, but the hourglass of that theme just works in some applications (like konqueror for example). On the Applications Menu for example I still get that jumping thing.
I tried to install my cursor theme in ~/.icons and also in /usr/share/icons ... but it doesn't make a difference.
Is there a way to get rid of this jumper? Please help me ... it makes me seasick ;-)

---

### Post by rbprogrammer on 2006-11-13
go to the K menu, then select [system settings].  up at the top of the window, click on [panel] and then on [launch feedback].  then just change the settings on the [bouncing cursor] group. 

all of this information is based on me assuming you have a problem with the bouncing icon.  i'm not sure if its a cursor theme problem, but i hope that helps...

---

### Post by zardoz on 2006-11-13
No wonder, that I couldn't find that option ..  cause it's not there.
I found at [http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html]("http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html") how it should look like, but in Kubuntu 6.10 (KDE 3.5.5) only the option "About Me", "Language", "Accessibility" and "Default Applications" in the subcategory "Personal" exists. No "Panel" there.
Is there an other way to get there?

---

### Post by zardoz on 2006-11-13
Ok ... its an official bug ... [https://launchpad.net/distros/ubuntu/+source/kde-systemsettings/+bug/67063]("https://launchpad.net/distros/ubuntu/+source/kde-systemsettings/+bug/67063") ... solution with "kcontrol", that could be get via shell.

---

### Post by Jucato on 2006-11-13
Press Alt+F2 and launch "kcontrol". Launch Feedback will be under Appearance & Themes.

---

