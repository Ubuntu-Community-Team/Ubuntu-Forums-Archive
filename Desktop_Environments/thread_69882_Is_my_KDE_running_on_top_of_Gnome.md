---
title: "Is my KDE running on top of Gnome?"
date: 2005-09-28
forum: Desktop Environments
---

### Post by twoseids on 2005-09-28
Newbie here, so maybe this is a dumb question. I notice that when I exit out of Ubuntu, my KDE desktop "minimizes", as it were, revealing my Gnome wallpaper, which then goes away too.  Is Gnome still running underneath my KDE?  Or am I just confused?

Also, is there any way I can just shut down from KDE?  When I exit, it merely brings me to the log-in screen, where I THEN exit.

Thanks!

---

### Post by Tilex on 2005-09-28
I don't think KDE is running over Gnome...in fact, when your wallpaper disappears, it's the login screen that shows up, so maybe that's why it seems like one run on top of the other.  
It is to be mentionned that linux is a mutli-user OS.  This means that you can open multiple user sessions at the same time, and have some of them run KDE, some other run Gnome.  So I don't think one run over the other since you chose at login time which desktop environment you want to start with. 
And regarding your second question, you just have to log off from your account and from the login screen, just shutdown the computer.

---

### Post by Paperjam on 2005-09-28
No, KDE and Gnome are two independent window-managers. I guess you are using gdm (gnome desktop manager) to login. If you prefer the KDE-look, you can use kdm (KDE desktop manager). So what you see when you log out is just a graphical manager for your login. I hope this doesn't confuse you even more :-)

---

### Post by f1dave on 2005-09-28
sounds like gdm is your display manager. If you want to shutdown from kde, you'll have to install kdm. But then you wont be able to shutdown from gnome as far as i know! So that's pretty much your choice there.

(lol, 3 posts within the same minute- how helpful is THAT? :P )

---

### Post by twoseids on 2005-09-28
[QUOTE=Tilex]I don't think KDE is running over Gnome...in fact, when your wallpaper disappears, it's the login screen that shows up, so maybe that's why it seems like one run on top of the other.  
It is to be mentionned that linux is a mutli-user OS.  This means that you can open multiple user sessions at the same time, and have some of them run KDE, some other run Gnome.  So I don't think one run over the other since you chose at login time which desktop environment you want to start with. 
And regarding your second question, you just have to log off from your account and from the login screen, just shutdown the computer.[/QUOTE]
No, it's not my login screen, it's my wallpaper from Ubuntu that displays.  THEN the login screen.  And yes, I'm using GDM, so that answers my second question.

The first question remains...

---

### Post by manicka on 2005-09-28
[QUOTE=twoseids]
The first question remains...[/QUOTE]

Using GDM causes this to happen. You can be assured that gnome isn't running beneath kde when you log in.

---

### Post by twoseids on 2005-09-28
[QUOTE=manicka]Using GDM causes this to happen. You can be assured that gnome isn't running beneath kde when you log in.[/QUOTE]
Okay, thanks manicka!  Curiosity satisfied.

---

### Post by Knome_fan on 2005-09-28
Hm, could also be nautilus running in the background.

Simply press Ctrl+Esc to see if nautilus is running and if it is, kill it.

---

### Post by twoseids on 2005-09-30
[QUOTE=Knome_fan]Hm, could also be nautilus running in the background.

Simply press Ctrl+Esc to see if nautilus is running and if it is, kill it.[/QUOTE]
It was, and I did.  Thanks! :)

---

