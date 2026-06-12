---
title: "Openoffice crashes with latest dist-upgrade"
date: 2005-05-31
forum: Desktop Environments
---

### Post by olicomber on 2005-05-31
Morning all,

I've a problem with Openoffice crashing on me at startup since doing a dist-upgrade on Friday.

The machine in question has had a fair bit of abuse, so I rebuilt it from scratch today.  It still has the same problem.

What happens is this: I start openoffice from the commandline.  It displays its splash, then its main window appears, pauses for a few seconds without displaying any menus etc, then it all disappears.  There is no error in the terminal, no coredump and no crash report dialog.

I'm wondering if this could be an X or font problem - If I run openoffice on the machine in question, but display the window on my workstation, it works fine.  In other words, it's only a problem when it is displaying its windows locally.

Many, many thanks in advance!

-Oli

---

### Post by olicomber on 2005-06-02
I've finally found the answer.  I've got a whole package set for building machines for people quickly, and had to wade through all the changes I made.

One change I was making was to introduce the option '--purge-delay=2000' to gnome-session to fix a problem I was having with the splash-screen not disappearing.  

I realise now the implication of this is that an application which takes more than 2 seconds to start and register with gnome-session, eg Openoffice on a Dell Optiplex, will be terminated.

Hope this info is useful to someone :0)

Cheers,
-Oli

---

