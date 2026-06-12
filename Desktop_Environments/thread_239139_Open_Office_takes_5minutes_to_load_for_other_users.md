---
title: "Open Office takes 5minutes to load for other users"
date: 2006-08-18
forum: Desktop Environments
---

### Post by linuxted on 2006-08-18
on my system, yet for me (the admin), it is seconds.  I'm referring to the spreadsheet, presentation or text editor applications.  I looked at top and see an occasional java service running on the other user's setup even when no other app (other than Open Office) was started.  I'm at a loss.  Any suggestions?

I made sure all the user privileges were enabled and still no luck

Thanks

](*,)

---

### Post by GuitarHero on 2006-08-18
Did you try running it from the terminal?  It may show you whats going wrong.

---

### Post by kerry_s on 2006-08-18
You could try> in open office>tools>options>memory> check the box under OpenOffice.org Quickstarter. log out and back in to take effect.

---

### Post by Nexusx6 on 2006-08-18
Have you tried adjusting the memory settings under Tool -> Options -> Memory for each user? I'm not sure if this would fix the problem, but when I upped the Graphics Cache to 25 megabytes OpenOffice starts ~4 seconds now.

Hope it helps :)

EDIT: Looks like Kerry_S was thinking the samething :-P

---

### Post by kerry_s on 2006-08-18
Yeah, upping the memory should also help. I have the "use" set to 256 and "memory" set to 20. Using the quicklauncher my openoffice opens instantly.

---

### Post by linuxted on 2006-08-18
> **GuitarHero said:**
> Did you try running it from the terminal?  It may show you whats going wrong.

from a terminal I get the following:
****************************************************
$ Xorg

Fatal server error:
Cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"

****************************************************

So I made (as root) a copy of /var/log/Xorg.0.log to /var/log/Xorg.0.log.old
and got the same message.

I tried creating a new user and the same thing happens!

---

