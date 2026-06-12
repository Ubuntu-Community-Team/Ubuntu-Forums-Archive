---
title: "KDE and GNOME integration - running KDE programs from GNOME"
date: 2005-10-28
forum: Desktop Environments
---

### Post by magnusbb on 2005-10-28
Hello,

I use GNOME daily, and am very satisfied with it. But sometimes, I want to use KDE applications, because there are many quality applications in the KDE branch. One is Konqueror, one is Kontact - and I also enjoy KOffice and especially the "coming star" Krita.

But when I launch a KDE app from GNOME a lot of memory is consumed due to loading various kde libraries (of course) - various kdeinits and kde-sockets also. But when I then close a KDE app, the libraries are still "lurking in the shadows". Is there a possibility to kill the KDE environment in one single operation - not involving a logout and login, or a manual process kill row?

---

### Post by HermanAB on 2005-10-28
I don't think that you need to worry about that.  Stuff that are not used, will eventually get swapped out if another process needs memory.  The Linux scheduler and memory manager are very good - relax and enjoy it!

Cheers,

H.

---

### Post by Joshya on 2005-11-19
How can I get Koffice to show up in the Gnome Menu.  I have tried several option the menu editor and have not been able to figure out the command.  I have KDE installed as well and have been able run koffice from the kmenu.

If it matters, I used synaptic to install Koffice before I put KDE on.

Any help will be greatly appreciated.

Josh

---

### Post by magnusbb on 2005-11-19
I can't find it in my menu. I suppose you'll have to add it manually. The commands are "kword", "kspread" and "kpresenter", I think.

---

### Post by taurus on 2005-11-19
The easiest and simpliest is to create an icon in the panel!!!  So when you want to run it, just click on it...

---

### Post by Talorgan on 2008-04-15
If there are now two desktops (I am a recent refugee from Windows) why can't we have KDE on one and GNOME on the other?

---

### Post by magnusbb on 2008-04-15
Was that supposed to be a joke? Actually, you can run every GNOME application in KDE and vice verse. I think it would be very confusing to have to desktops with different "usability philosophies" running at the same time. But, also that is possible: you could run KDE (or GNOME) like you normally would and then start the other environment in a nested X-Server (see Xnest for more).

**Just as an update to the original post: ** the situation has not change very much in that respect, apart from that I have switched to KDE. It works better that way. Funny to see my old post brought back to life. :)

---

### Post by Talorgan on 2008-04-15
> **magnusbb said:**
> Was that supposed to be a joke?

A light-hearted suggestion perhaps.

;-)

> **magnusbb said:**
> Actually, you can run every GNOME application in KDE and vice verse

Hmmm!

I'll need to investigate this further. I've been switching back and forth between desktops, but from what you say this might not be necessary.

---

### Post by magnusbb on 2008-04-15
Yes, the programs should be in your menu. This should be absolutely no problem. What I was complaining about in 2005, was just the memory footprint when having these two environments up and running at the same time, but this is a minor problem today as we usually have more memory in our computers.

---

