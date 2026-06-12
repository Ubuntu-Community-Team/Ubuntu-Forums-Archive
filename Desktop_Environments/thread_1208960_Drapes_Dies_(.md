---
title: "Drapes Dies :("
date: 2009-07-09
forum: Desktop Environments
---

### Post by neilblue on 2009-07-09
Hello,

I have previously used Drapes and Wallpaper-tray in ubuntu. But now I am running 9.04 when I try to start Drapes I get this error in the logs:

Passing command-line arguments in .server files is deprecated:

From google it seems to be related to mono. Does anyone else have this problem or know of a fix?

Thanks
Neil

---

### Post by directhex on 2009-07-09
I can't reproduce a problem, drapes starts fine here

---

### Post by dccrens on 2009-10-27
I have the exact same thing. I have three different Jaunty systems. On two of them, I installed clean and drapes works fine. On the third system (which is my main server) I upgraded to 9.04 from 8.10 and on that machine drapes will not run. I get the same error. ( Passing command0line arguments in .server files is depreciated: "/usr/bin/drapes --panel-applet" )

Has anyone else seen this? I do not what to reload the machine just to get wall paper changing working...

---

### Post by directhex on 2009-10-27
Okay, I see what's causing the bug. I'll try to get around to it. There needs to be a new drapes-applet launcher in /usr/bin, and the bonobo server file needs to use it, not drapes with --panel-applet on the end

---

### Post by directhex on 2009-10-28
Wait, I forgot, Drapes isn't pkg-cli-apps so I can't do anything with it. File a bug in Debian/Ubuntu. The fix is that a new launcher script is needed, drapes-panel, which works around the inability of calling "/usr/bin/drapes --panel-applet" - see also Novell bug 264696

FWIW, it's NOT a Mono bug, it's an app bug (in that the app uses behaviour removed from the GNOME library "Bonobo")

---

