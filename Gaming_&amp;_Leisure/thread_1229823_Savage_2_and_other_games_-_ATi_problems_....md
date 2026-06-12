---
title: "Savage 2 and other games - ATi problems ..."
date: 2009-08-02
forum: Gaming &amp; Leisure
---

### Post by YukaToshi on 2009-08-02
I have been trying to wean a friend of Windows XP as he has been having problems with it, and I felt that Ubuntu would be the perfect replacement. So I finally convinced him to let me take his laptop and set up Ubuntu Hardy 8.04.3 LTS 64 bit on it. However it has an ATi X1250 integrated chip which is providing me with a lot of problems. I have fully installed the driver from ATi's site (Catalyst 9.3), but it is having trouble with most of the games I am trying to install. By far the worst is Savage 2 which won't even start, it gives this error;

rakameire@aprya:~$ /usr/local/games/Savage2/savage2.bin
warning: The VAD has been replaced by a hack pending a complete rewrite
Savage2 - Fatal Error: OpenGL 2.0 not available.
Segmentation fault
rakameire@aprya:~$ 

Now I know that this used to be a problem with an older version of Savage 2 but this is the new version that I have fully updated manually from Terminal. 
Also Heroes of Newerth has less than half the performance that it did under Windows XP. It's really slow and has issues with water not being correctly rendered, it's just black. 
Returning to the desktop leaves half of the top taskbar black, and you need to logout and back in again to get rid of it. Compiz doesn't work properly and I have to disable it.

I really don't want to be defeated in converting my friend to Ubuntu by ATi's horrible drivers, so does anyone know of anyway I can fix these issues?

---

### Post by juancarlospaco on 2009-08-02
Check the Savage 2 Forums, its a workaround, and fix.

you need to **run savage server**, and then on the savage server CLI run "**checkforupdates**",
**wait 30 minutes** to download and install updates,** run savage client**.

Its because you don't have OpenGL 2, you are using OpenGL 3 capability.
Its a game problem, not drivers problem this time.

If still don't work, uninstall and download the whole game again.

Im "juancarlospa" at savage 2 :)

---

### Post by YukaToshi on 2009-08-02
> **juancarlospaco said:**
> Check the Savage 2 Forums, its a workaround, and fix.

you need to **run savage server**, and then on the savage server CLI run "**checkforupdates**",
**wait 30 minutes** to download and install updates,** run savage client**.

Its because you don't have OpenGL 2, you are using OpenGL 3 capability.

Hi.
I know this as I play Savage 2 and have had to do this before. It is fully updated but still having the same problem!

---

### Post by juancarlospaco on 2009-08-05
Full Reinstall from scracht... 
:)

---

