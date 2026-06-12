---
title: "Is Xubuntu more responsive in LTSP environment than Gnome (Edubuntu)?"
date: 2007-10-30
forum: Desktop Environments
---

### Post by Athanasius on 2007-10-30
If I used Xubuntu as a ltsp server would it be more responsive on the side of the terminals compared to Gnome?  Gnome has been constantly crashing on the terminals in Gutsy and I wonder if things would just be faster?

---

### Post by scrooge_74 on 2007-10-30
What do you mean LTSP? Are you refering to Dapper (Ubuntu 6.06)?

Usually Xubuntu is faster is that is what you area asking.  Some people are experiencing problems with Gutsy

---

### Post by Athanasius on 2007-10-30
I mean in a server setup, if it has less "overhead" than gnome then would the clients be faster?

---

### Post by carlos1992 on 2007-10-30
xubuntu i just the same speed that Gnome the only difference is the installation requeriments but if you have196 mb then it's going to be as slow as gnome
i used it and switch back to Gnome

---

### Post by Athanasius on 2007-10-30
Ok, thank you very much, that is what I wanted to know.:)

---

### Post by scrooge_74 on 2007-10-30
> **carlos1992 said:**
> xubuntu i just the same speed that Gnome the only difference is the installation requeriments but if you have196 mb then it's going to be as slow as gnome
i used it and switch back to Gnome

Not quite right, if you have Gnome install at the same time you install Xfce4 you are going to have Gnome services running in the background even if you are using Xfce4 as your GUI.  if you install a pure Xfce4 it is going to be a lot faster.

In a PC  with 512 MB Xfce4 is a lot faster than Gnome, with 196 MB Xfce4 would probably be as fast as Gnome with double the RAM. I have a Toshiba running with pure Xfce4 due to only having 256MB and Gnome been a little slow.

---

### Post by carlos1992 on 2007-10-30
Dude that's probably because of sservices but ubuntu isn't faster or slower than xubuntu the only way to make it faster is with fluxbox or thing like that
i'm comparing flavors with the same services and in the same computer,

---

### Post by scrooge_74 on 2007-10-30
Well I am comparing using Ubuntu then Ubuntu/Xbuntu and then Xubuntu on the same laptop: Xubuntu by itself is a lot faster than regular Ubuntu. If then you are talking about using another WM as fluxbox then I can tell you ICEwm i think is even faster (but I am too lazy to config the menus)

But between using Xubuntu and Ubuntu, Xubuntu is a little faster, if you try then Debian Etch using only Xfce4 is even faster than regular Ubuntu or Xubuntu

---

### Post by MarcDM on 2007-10-31
> **Athanasius said:**
> If I used Xubuntu as a ltsp server would it be more responsive on the side of the terminals compared to Gnome?  Gnome has been constantly crashing on the terminals in Gutsy and I wonder if things would just be faster?

Short answer : YES.
Long Answer : 

XFCE uses GTK widgets yes. and some of the gnome themes work too. If you run *gnome-settings-daemon* in the background, then all your gtk apps will use the theme you've selected. 

The people that say that XFCE is no faster than Gnome is because they're only running gnome apps. For starters, Thunar is waay faster than Nautilus. The menu/panels infrastructure is also more lightweight. 

The speed increase you'll notice on the client is because the server needs to use less resources to run the software on the client. 

What's nice about Ubuntu is that you don't need to re-install to use Xubuntu. just 
apt-get install xubuntu-desktop. 

Or do what I did, apt-get install xubuntu-desktop and then say no. And then pick out specific apps from the list to install. That way I get a super lightweight system.

Oh and I'm not talking theory here. I multiple terminal clients using Feisty under a Xen DomU. XFCE is just plain faster. Especially the login process.

---

### Post by RedSquirrel on 2007-10-31
OP: Xubuntu is still pretty heavy. A light window manager such as Fluxbox, IceWM, Openbox might be better. It would certainly consume fewer resources.

You can also have a look at the xfce4 metapackage. That is just the core of Xfce. The xubuntu-desktop package pulls in all of the applications and other stuff.


> **carlos1992 said:**
> xubuntu i just the same speed that Gnome the only difference is the installation requeriments but if you have196 mb then it's going to be as slow as gnome
i used it and switch back to Gnome

Xubuntu is faster than Ubuntu on older systems. On newer systems with lots of RAM, everything will be fast and you probably won't see much difference between Xfce, GNOME, KDE, etc.


> **MarcDM said:**
> Short answer : YES.
Long Answer : 

XFCE uses GTK widgets yes. and some of the gnome themes work too. If you run *gnome-settings-daemon* in the background, then all your gtk apps will use the theme you've selected. 

If you don't want to use gnome-settings-daemon, you can use gtk-theme-switch or gtk-chtheme. They're in the repositories. gtk-chtheme is only on gutsy. These programs create the file ~/.gtkrc-2.0. You only have to run them when you want to change the theme. You can also create this file yourself, but you have to know the correct settings to put in there.

---

### Post by scrooge_74 on 2007-10-31
Check this [howto]("http://www.psychocats.net/ubuntu/purexfce") for pure Xfce under Ubuntu

---

### Post by Gremlinzzz on 2007-10-31
If you have low ram give this a shot.
[http://distrowatch.com/?newsid=04562](http://distrowatch.com/?newsid=04562)

---

