---
title: "[KDE] KATE starts everytime I log into KDE"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Chareos on 2006-08-20
Hi all,

no matter what I try (start kde with blank session) KATE starts itself when I login to KDE.
It also opens, apart documents I left open in it (good), two other documents.
If I close 'em and relog, same thing, kate starts with these two documents opened along with good ones.

Any suggestions ?

---

### Post by aysiu on 2006-08-20
Alt-F2 ```
kcontrol
``` Then match this screenshot.

---

### Post by Chareos on 2006-08-20
Already there... that's why it's so strange.
Already tried to move it, relog, move back on blank session and relog... same problem.

---

### Post by aysiu on 2006-08-20
> **Chareos said:**
> Already there... that's why it's so strange.
Already tried to move it, relog, move back on blank session and relog... same problem.
And you have these as your Kate settings, too?

---

### Post by Chareos on 2006-08-20
I'll try.
(if it works... it's a shame I can't just open kate with last used docs without this annoying autostart at login).

I'll let you know.
THANKS for suggestions and time (even screenshots... you really took care about the problem, man !)

---

### Post by Chareos on 2006-08-23
No, it didn't work.

---

### Post by aysiu on 2006-08-23
The only thing I can think of is to reset your KDE settings. Unfortunately, this will reset *all* of your KDE settings, unless you can isolate those pertaining to this particular issue.

If you're interested, do ```
mv ~/.kde ~/.kde.old
``` and log out and log back in again.

If that doesn't work, you can restore your old settings by doing ```
rm -rf ~/.kde
mv ~/.kde.old ~/.kde
``` and log out and log in again.

---

### Post by km3k on 2007-11-06
This is really late, but I just had this problem and figured it out. If you have any file in .kde/Autostart that isn't a .desktop file, it will open that file in its default program. I had a script in there that I was referencing from a .desktop file, so not only did the script run, but kate also opened the script as a text file at login. Hopefully this will help someone else.

---

### Post by Mithrilhall on 2007-11-06
Just out of curiosity, but when you logoff/shutdown/reboot is Kate open? Try opening a console and issue this command and see if Kate is running in the background.

```

ps -e | grep kate

```

---

### Post by km3k on 2007-11-06
Kate was not running and it was set to use a new session at login anyway. What tipped me off was that it was opening the script that I had placed in .kde/Autostart

---

