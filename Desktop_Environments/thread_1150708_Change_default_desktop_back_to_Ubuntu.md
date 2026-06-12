---
title: "Change default desktop back to Ubuntu"
date: 2009-05-06
forum: Desktop Environments
---

### Post by howardf42 on 2009-05-06
I recently installed KDE on top of Ubuntu 9.04 and although I like some of the KDE interface, I'd like to return to the more familiar Ubuntu desktop as a default.  How can I get Ubuntu back as the default at bootup?

---

### Post by oldrocker99 on 2009-05-06
On the login screen, select "Sessions." Hit GNOME. Log in as usual. You'll get a requester asking if you want to log in to Gnome for this session only, or Make Default.
Hit Make Default, and you'll have Gnome come up whenever you log in.

:guitar:

---

### Post by howardf42 on 2009-05-06
> **oldrocker99 said:**
> On the login screen, select "Sessions." Hit GNOME. Log in as usual. You'll get a requester asking if you want to log in to Gnome for this session only, or Make Default.
Hit Make Default, and you'll have Gnome come up whenever you log in.

:guitar:

I had been doing that, but the requester never shows up to Make Default.  Am I missing something?

---

### Post by howardf42 on 2009-05-08
> **howardf42 said:**
> I had been doing that, but the requester never shows up to Make Default.  Am I missing something?

I guess I'm still missing the Make Default dialog.  Does anyone know how to find that again?  My base system is Ubuntu, but Kubunto is loading as default and I'd like to change back to Gnome at startup.  What am I missing?

---

### Post by kanikilu on 2009-05-08
Assuming you're still using GDM, try running the following from a terminal:
```
gksu /usr/sbin/gdmsetup
```
If you are in Gnome, you can also get to this from System > Administration > Login Window. Under the General tab, you should be able set the default session back to Gnome.

---

### Post by howardf42 on 2009-05-08
> **kanikilu said:**
> Assuming you're still using GDM, try running the following from a terminal:
```
gksu /usr/sbin/gdmsetup
```
If you are in Gnome, you can also get to this from System > Administration > Login Window. Under the General tab, you should be able set the default session back to Gnome.

I think therein lies the problem.  Although it wasn't intentional, KDM is loading at startup instead of GDM.  How can I change that?  I think that will solve my problem.

Thanks for the help.

---

### Post by kanikilu on 2009-05-08
I think this should do it:
```
sudo dpkg-reconfigure gdm
```

---

### Post by howardf42 on 2009-05-08
> **kanikilu said:**
> I think this should do it:
```
sudo dpkg-reconfigure gdm
```

Bingo!  That did it.  Muchas gracias, amigo.

Although The Gnome login screen comes up and loads properly, the system is booting Kubuntu and shutting down Kubuntu at the end of the day.  I guess that isn't a problem, but I'm confused.  Why isn't the Ubuntu progress bar showing instead of kubuntu?

Perhaps a minor point, but the session change dialog is telling me that my default is loading Xclient scripts, not Gnome directly.  It seems to work the same either way.  What are the Xclient scripts supposed to do?

---

### Post by howardf42 on 2009-05-09
I'm sorry if this is a double post violation, but I realized that my edited message earlier may be missed by some, so here's the same message posted separately.  Sorry if some of you see this twice.

Although The Gnome login screen comes up and loads properly, the system is booting Kubuntu and shutting down Kubuntu at the end of the day. I guess that isn't a problem, but I'm confused. Why isn't the Ubuntu progress bar showing instead of kubuntu?

Perhaps a minor point, but the session change dialog is telling me that my default is loading Xclient scripts, not Gnome directly. It seems to work the same either way. What are the Xclient scripts supposed to do?

---

