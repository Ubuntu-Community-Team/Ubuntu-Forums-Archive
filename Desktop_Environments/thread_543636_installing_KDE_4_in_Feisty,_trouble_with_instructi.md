---
title: "installing KDE 4 in Feisty, trouble with instructions."
date: 2007-09-05
forum: Desktop Environments
---

### Post by wickstopher on 2007-09-05
Hello!  I'm trying to install KDE 4 in Kubuntu Feisty, and I've made it through almost all of the instructions on the kubuntu site.  I can choose KDE 4 in my sessions when I login, but it doesn't work.  I get a black screen for a few seconds, and then it takes me back to the login screen.  The only instruction that I don't understand is the last one, which states

> put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.


I'm not sure which "export lines" they're talking about, and I'm assuming the reason that I can't start a KDE 4 session is because I haven't completed this step.  Any help out there?

---

### Post by Eazy© on 2007-09-05
I got problems to with this. I get something like "could not find xsession, falling back to default, or something like that (I'm tired) Would be nice if someone could make a clearer guide. :)

---

### Post by happysmileman on 2007-09-05
> export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4

Those are the 4 export lines

---

### Post by Eazy© on 2007-09-05
From this ["howto"]("http://kubuntu.org/announcements/kde4-beta1.php")
I did this:

To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.

But not this:

To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.
as I thought didn't needed to?

---

### Post by wickstopher on 2007-09-06
Great, thanks.  After pasting those four lines in, I was able to start a KDE 4 session.  It's ugly as sin, though, at least starting out (and what's the deal with that group photo on startup?!?), and seeing as I'm already late getting to bed, I'll mess around with it more tomorrow in hopes that I can make it look a little better.  Admittedly, I'm really tired, and I was only in there for about 30 seconds before I logged out in dismay without really having tried anything, but for now I'll stick to KDE 3.5.6.

---

### Post by argotnaut on 2007-09-13
> To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop

I have no kde.desktop file in /usr/lib/kde4/share/apps/kdm/sessions/ ! The only thing in there is a folder called 'pics.' Anyone know what's wrong here? I guess I'll try uninstalling and reinstalling in the meantime.

---

### Post by argotnaut on 2007-09-13
Aha, it's because I was following old instructions for beta 1, which said to download kdebase-dev (current instructions are to download kdebase-workspace). Now I have everything in the right place, but having the original problem posted here -- xserver keeps restarting and dumping me back to the login page. I did add those 4 lines, but maybe I put them in the wrong file or something; I'm getting a bit tired. :) Maybe I'll try again later tonight and double-check everything. After backing some stuff up, though, I think.

---

