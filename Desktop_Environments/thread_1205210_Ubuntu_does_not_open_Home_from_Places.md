---
title: "Ubuntu does not open Home from Places"
date: 2009-07-05
forum: Desktop Environments
---

### Post by angelot on 2009-07-05
When clicking Places->Home (or any of my bookmarks) I get this errormessage:
[IMG]http://www.smb-data.net/Skjermdump-Feil.png[/IMG]
The message is in norwegian and say something like "Can not open ... No application is registered to handle this file"
I have no problems opening nautilus from my desktop or from the Home- (or "My computer-") icon on the desktop.
It's only the "links" under Places (top panel>menuline/applet).

This might happend when I installed Jaunty for the second time - not formatting the /home partition. I have no problem accessing my /home-folder either...

Thanks!

Bump: Anyone?

---

### Post by angelot on 2009-08-09
After some googling I found the solution...

It seems that nautilus "forgets" which program (e.g nautilus) to use when opening folders...

1. Open Nautilus (or hit Alt+F2, then type nautilus)
2. When Nautilus opens, right-click on a folder and choose "open with..."
3. Browse for an app and scroll down till you get to nautilus then hit OK.
4. Close Nautilus and try again. Should work OK now.

---

