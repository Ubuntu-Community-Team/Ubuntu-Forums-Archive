---
title: "Problem recovering from AIGLX"
date: 2006-09-04
forum: Desktop Environments
---

### Post by FJ_Sanchez on 2006-09-04
Hello, I use Kubuntu and last night I changed my system to use aiglx+compiz. It's not the first time I switch between aiglx and normal xorg server. I changed next files:

/etc/enviroment --> add KDEWM=compiz-start
/etc/kde3/kdm/kdmrc --> Change the server option ServerCmd=/usr/bin/Xorg :0 to ServerCmd=/usr/bin/Xorg-air :1
I also changed my xorg.conf because I normally use fglrx and I changed this and all the needed stuff but I backup the original.

After Ctrl+Alt+BackSpace this worked correctly, AIGLX was running with compiz as always. But When I tried to recover my old config I got problems.

All runs normal but when KDM loads doesn't show any icon of loading and when you login it goes directly to failsafe (doesn't mind what you choose). If I manually run kicker, kwin, kdesktop, etc it runs, but it doesn't start automatically.

Looking at syslog there are some things weird:

Sep  4 12:40:57 localhost kdm_greet[5154]: Can't open default user face
Sep  4 12:41:15 localhost kdm_greet[5154]: Internal error: memory corruption detected
Sep  4 12:43:31 localhost kdm[5068]: X server for display :0 terminated unexpectedly

I also notified that a line was missing in /usr/share/autostart/kdesktop.desktop: I added this line X-KDE-autostart-phase=0 because I think it should be there but I'm not sure.

Now I cannot run with or without aiglx normally.
Can anyone help me?

---

