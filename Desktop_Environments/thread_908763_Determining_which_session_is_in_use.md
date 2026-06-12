---
title: "Determining which session is in use?"
date: 2008-09-02
forum: Desktop Environments
---

### Post by geminidomino on 2008-09-02
I'm trying to write some scripts for doing some things when I login, but some of them (notably, changing the background) depend on which session type, GNOME or KDE, I'm using.  

Is there a way to programatically determine which one is in use on the command line?

Update: Nevermind. Found a kludgy way to pull it off.

if [ `pgrep  kdesktop -u $USER` ];
then
WM=KDE
fi

if [ `pgrep  gnome-session -u $USER` ];
then
WM=GNOME
fi

---

