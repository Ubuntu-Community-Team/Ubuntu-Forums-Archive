---
title: "Using GDM on Kubuntu"
date: 2006-06-12
forum: Desktop Environments
---

### Post by DrQuincy on 2006-06-12
I'm running Kubuntu but am using GDM istead of KDM so that I can run Compiz.  Could someone please clarify this implications of this?  I understand that I cannot run KDE themes but will this pose any problems running KDE applications?  What are the limitations of this setup?

Thanks.

---

### Post by asimon on 2006-06-12
Actually you should be able to use compiz with kdm too, IIRC instructions for it are buried somewhere in [this thread](http://www.ubuntuforums.org/showthread.php?t=148351).
(sorry, I don't use compiz, and can't give you instructions myself).

Anyhow, you can use GDM just fine with KDE. There are no implications, everything will work. The only thing which you will loose it the ability to reboot or halt the computer directly through KDE's logout dialog. With GDM KDE only offers you the option to end the session, you need to use GDM's menu to reboot/halt the machine.

It's right that you can not use KDM themes with GDM. Both login managers use slightly different theme formats. But this is only affects the login manager, other themes in KDE, styles, colours, etc. will work just fine.

---

### Post by DrQuincy on 2006-06-12
Thanks a lot for your reply.  That's strange that Baghira doesn't work under it then (all the window decorations disappear).

What exactly is the differennce between KDM and GDM then?

---

### Post by asimon on 2006-06-12
[QUOTE=DrQuincy]That's strange that Baghira doesn't work under it then (all the window decorations disappear).[/quote]
Oops, yes I forgot. You're right, Compiz draws it's own window decorations.

[QUOTE=DrQuincy]
What exactly is the differennce between KDM and GDM then?[/QUOTE]
Well, from a user's point of view they are indeed very similar. KDM is the login manager of KDE, GDM the login manager of Gnome, KDM uses Qt and KDE libraries, GDM is build upon GTK+ and some gnome libraries, etc. See [this mail](http://lists.debian.org/debian-devel/2004/09/msg01494.html) for a comparison. It's somewhat outdated (for example KDM back then didn't supported themes as it does today), but you get the idea.

---

### Post by DrQuincy on 2006-06-12
Thanks again.

So, should I be looking for Gnome themes then or are there special Compiz ones?

Thanks.

---

### Post by rogeriovinhal on 2006-06-12
I am using GDM with KDE, and I CAN reboot and shutdown from KDE...

I'm using GDM because KDM freezes many times when I try to shutdown or reboot... With GDM everything is ok.

---

