---
title: "Ubuntu with Gnome / Libreoffice"
date: 2015-05-10
forum: Desktop Environments
---

### Post by RogerDavis on 2015-05-10
I have a launch icon on the desktop for this.  It used to work, until the latest(?) update.  I can't find what I had to do before to make this work, I had the same problem when originally placing it on the desktop.  When I click the icon, I get "The application launcher “libreoffice-startcenter.desktop” has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe."

I tried to click the box "Allow executing file as program", but it is greyed out, so is unresponsive.

How do I fix this?

---

### Post by dino99 on 2015-05-10
Also got that annoying message a few times; but does not know the real reason. The packages now have to be signed (trusted source), but usually its done all the time with the ubuntu archives, and ppa are also signed. Maybe its an issue when the application is installed from the source (untrused third party), but i never use such source, and have met that issue too; so i'm still searching what is wrong (maybe a plugin or an own macro).

---

### Post by RogerDavis on 2015-05-10
Figured out an answer:
- Open Terminal
- Type "sudo nautilus" (not the ")
- Ignore the messages, go to the opened Nautilus
- Open the Desktop folder
- Find the icon for LibreOffice
- Right click the icon
- Select "Properties"
- Click the "Permissions" tab
- Check the box by "Allow executing file as program"
- RESTART

Should now work.

---

