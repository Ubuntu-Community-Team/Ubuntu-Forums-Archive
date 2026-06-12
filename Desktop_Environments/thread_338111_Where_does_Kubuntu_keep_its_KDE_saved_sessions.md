---
title: "Where does Kubuntu keep its KDE saved sessions ?"
date: 2007-01-14
forum: Desktop Environments
---

### Post by DaveQB on 2007-01-14
It seems Kubuntu doesn't keep them in the standard KDE locations.

I had trouble with my session crashing after about 5-6 windows/applications were restored.  Of course this worked

```

mv ~/.kde ~/.kdeOLD 

```

But I don't want to have to reconfigure all of my KDE just because of one borked session.

So I did this next while logged out of KDE and through a VT

```

mv ~/.kde ~/.kdeNEW
ln -s ~/.kdeOLD ~/.kde
rm -rf ~/.kde/share/config/sessions/*
rm -f ~/.kde/share/config/ksmserverrc

```

logged in again and NO DIFFERENCE.

Session still restored as before and crashed, as before.

I asked on #kde and they said I did everything right and it must be a Kubuntu change to KDE.

So where does KDE keeps its per user saved sessions ?

Thanks

---

### Post by freaker2k4 on 2007-01-14
Hello, I just wanted to ask the same question, but abot Ubuntu and Gnome, because i want to backup my gnome-panel view and can't find the file where this kind of data is stored.

---

### Post by DaveQB on 2007-01-15
bump

---

### Post by DaveQB on 2007-01-17
bump

---

