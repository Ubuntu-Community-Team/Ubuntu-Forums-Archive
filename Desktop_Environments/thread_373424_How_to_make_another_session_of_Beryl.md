---
title: "How to make another session of Beryl ?"
date: 2007-03-01
forum: Desktop Environments
---

### Post by MaximB on 2007-03-01
I've fallowed this guide and made a Gnome Beryl session : [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

now I want to create a **separate** KDE Beryl session.
how do I do this ?

P.S
I have ATI radeon 9800 Pro Video Card.
and running Ubuntu Edgy.

I already have a normal Gnome and KDE sessions.

---

### Post by c0nv1ct on 2007-03-01
I did the same as you.  Used that guide to setup Beryl in gnome.  I then decided to install the Kubuntu packages and mess around with KDE.  To get Beryl to run, all I did was add a link to beryl-manager to my .kde/Autostart folder.  It was working fine, but now beryl-manager starts, and Beryl isn't the default window manager.  I have to manually select it from the menu every time I log in.

I'm not sure if thats the proper way to do it, but it was working fine at one point, i probably just messed up the default window manager somewhere.

Edit: I fixed the problem of Beryl not being default.  I just went into emerald, changed themes, then logged back in.  Works fine now.  It actually seems to run better in KDE for some reason.

---

### Post by MaximB on 2007-03-02
sorry, I'm not so familiar with KDE just yet
were is the start folder ? how do I add it to there ?
I know in Gnome you can add it to sessions>startup programs.
but KDE... ?

---

### Post by c0nv1ct on 2007-03-02
> **MAXDDARK said:**
> sorry, I'm not so familiar with KDE just yet
were is the start folder ? how do I add it to there ?
I know in Gnome you can add it to sessions>startup programs.
but KDE... ?

make a link in ~/.kde/Autostart

so, something like this:

```
ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager
```

---

### Post by MaximB on 2007-03-02
I've made it, but it's not working, I don't even think it's supposed to work.
you see, only my XGL session actually use beryl
but if I run the beryl-manager im regular gnome and then switch the manager to beryl - nothing happens.
it's a matter of session.

I think we need to find other way.

---

### Post by c0nv1ct on 2007-03-02
I'm not sure I understand.  Are you running KDE in XGL?  How are you starting KDE?  from the GDM session options?  My gnome and KDE run in the same X session, i'm not sure how you have it setup.

---

### Post by MaximB on 2007-03-02
well, I have a separate session for Gnome, KDE and XGL(Gnome XGL).
so if I want Gnome Beryl I run the XGL session.
if I run regular gnome session and then run beryl-manager and try to switch to beryl - it would do nothing, same thing in KDE.

---

### Post by c0nv1ct on 2007-03-02
Have you tried going [here]("http://www.ubuntuforums.org/showthread.php?t=127090") to try and setup XGL for KDE?

---

