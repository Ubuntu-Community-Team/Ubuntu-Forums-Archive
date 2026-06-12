---
title: "Beryl Help!!"
date: 2006-10-10
forum: Desktop Environments
---

### Post by marco999 on 2006-10-10
Hello everyone,

I have a Compaq Presario 2170US and I have Ubuntu Dapper installed on it. I installed XGL and Beryl installed on it. I followed the guide entitled ATI Mobility XGL/Compiz Radeon, except when it came to installing compiz I installed Beryl instead. This was all fine until I decided to use "sudo shutdown -h now" in a shortcut launcher on the desktop. I was dissmayed to find out that Beryl does not load now when I login with XGL.

I even tried launching Beryl via the terminal in XGL this is what happend:

I entered the command "beryl" into the Terminal Pressed Enter.
Beryl launched but without any titlebars.

As of yet I am unable to launch Beryl this way, if you can help me plz do so.

As per my problem above please give me some advise as to how I should resolve this very annoying and very nasty problem.

Marco999

---

### Post by marco999 on 2006-10-10
Can Somone Tell nme how to fix this problem?????? Or at least how to make Compiz work instead of Beryl????????????????????/



Marco999

---

### Post by astoltz on 2006-10-10
I think the correct command is "beryl-manager". You may have to install the beryl-manager package before it'll work.

---

### Post by marco999 on 2006-10-10
I installed that and when I run it it says that it is already running....

Tho it does not start when I login to XGL nor any other Desktop.

Plz help

Marco999

---

### Post by astoltz on 2006-10-10
Do you have a little Beryl icon in the system tray?  If you click that, you can pick the window manager.  Sometimes when I login, Metacity is started instead of beryl but it's easily switched via that tray icon.

---

### Post by marco999 on 2006-10-10
I do not have that icon, how can I get it to appear?

---

### Post by marco999 on 2006-10-10
Also I should tell u that the XGL that I see looks alot like GNOME. It even has the same menus and titlebars which is not right.... Is there a way to change the windows manager via the Terminal? Also what do you have in startup for the sessions window related to Beryl?


Marco999

---

### Post by marco999 on 2006-10-10
Caling all Ubuntu XGL/Beryl ATI users!!!!

How do I fix this issue?????? (look at post #1): there is no system tray icon.

---

### Post by astoltz on 2006-10-10
Gnome is NOT a window manager, it is a Desktop environment.  By default, gnome uses Metacity as it's window manager.  Beryl replaces metacity - it does not replace gnome so you'll still see the gnome menus, panels, desktop, etc.  I know this is not your question but there seems to be a little confusion.

In the gnome panel, have you added the applet that shows the system tray?  I don't use gnome but I think it's called "system notification area".  Also when you run the command "beryl-manager" what is the error that you get?

---

### Post by marco999 on 2006-10-10
Thanks I now have added the Notification area and the icon now appears! *Jumps up and down in thanks* I can now switch inbetween the differen't window managers :D 

Marco999

---

