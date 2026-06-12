---
title: "Change display manager?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by maxsideburn on 2005-04-21
How can I change my display manager? Ubuntu doesn't have a system control panel like in Mandrake.

---

### Post by Kimm on 2005-04-21
I supose you mean that you want KDE instead of GNOME...

just open the console and type:

sudo apt-get install kde

then, when it finnishes, restart the X server and select "KDE Session" at the login screen, then chose "Make default" when it askes you. Woala you are now in KDE...

---

### Post by XDevHald on 2005-04-21
Hmm, such as changing how it looks, such as themes and etc? if so it's in your **System > Administration > Themes**

---

### Post by bored2k on 2005-04-21
[QUOTE=maxsideburn]How can I change my display manager? Ubuntu doesn't have a system control panel like in Mandrake.[/QUOTE]
 If Ubuntu had Mandrake Control Panel, it wouldn't be Ubuntu, right ?
System > Administration > Login Screen setup is all you need.

There's also gnome-control-center, but it doesn't work on that.

---

### Post by maxsideburn on 2005-04-21
No what I meant was not how I change to a different UI, but how do I change the DM? I installed the WDM and want to use it instead of GDM.

---

### Post by siebzehn on 2005-04-21
[QUOTE=maxsideburn]How can I change my display manager? Ubuntu doesn't have a system control panel like in Mandrake.[/QUOTE]
 If you don't like gdm  just  apt-get install kdm

I'm not sure if you have to remove gdm, in debian you don't.  Once you install a different display manager, debconf asks you wich one you want to use.

If you already have installed gdm and kdm,  just   dpkg-reconfigure gdm  (or kdm), choose the one you want to use

---

### Post by siebzehn on 2005-04-21
[QUOTE=siebzehn]If you don't like gdm  just  apt-get install kdm

I'm not sure if you have to remove gdm, in debian you don't.  Once you install a different display manager, debconf asks you wich one you want to use.

If you already have installed gdm and kdm,  just   dpkg-reconfigure gdm  (or kdm), choose the one you want to use[/QUOTE]


You can do the same with wdm

---

### Post by bored2k on 2005-04-21
> 
# cd /etc/X11/
root@noir:/etc/X11 # cat default-display-manager
/usr/bin/gdm


Just change this to wdm

---

### Post by Cool_dude_Prav on 2005-04-21
Is it possible to change the Desktop Environment just before login as can be done on IceWM???

The existing ones are FailSafe and Default...

---

### Post by siebzehn on 2005-04-21
[QUOTE=Cool_dude_Prav]Is it possible to change the Desktop Environment just before login as can be done on IceWM???

The existing ones are FailSafe and Default...[/QUOTE]
 Yes it is, but you have to install the desktop or windows enviroment.

I use XFCE4, if you want to use it just   sudo apt-get update xfce4

And then you can choose it from the login screen.

---

### Post by fdoving on 2005-04-21
[QUOTE=bored2k]Just change this to wdm[/QUOTE]
 .. just adding that the 'proper' (debianized) way of doing that, is 'sudo dpkg-reconfigure wdm' and choose it from the list you'll be prompted with.

- Frode

---

### Post by Cool_dude_Prav on 2005-04-22
[QUOTE=siebzehn]Yes it is, but you have to install the desktop or windows enviroment.

I use XFCE4, if you want to use it just   sudo apt-get update xfce4

And then you can choose it from the login screen.[/QUOTE]
 I want to access either my GDM or my KDM which i will choose when I get ready to log-in...

How can I do this?

I have only the KDM, FailSafe and Default ones in "Session Type" even though GDM is installed, it doesn't show in the list of session types.. unlike IceWM, which can be seen

---

### Post by fdoving on 2005-04-22
[QUOTE=Cool_dude_Prav]I want to access either my GDM or my KDM which i will choose when I get ready to log-in...

How can I do this?

I have only the KDM, FailSafe and Default ones in "Session Type" even though GDM is installed, it doesn't show in the list of session types.. unlike IceWM, which can be seen[/QUOTE]
 GDM is a display manager like KDM.. it's not a session manager/desktop environment like gnome, kde, icewm, etc.

It's not ment to be in the list. You can choose to use either KDM or GDM, you can not start GDM from KDM.

- Frode

---

### Post by Cool_dude_Prav on 2005-04-22
[QUOTE=fdoving]GDM is a display manager like KDM.. it's not a session manager/desktop environment like gnome, kde, icewm, etc.

It's not ment to be in the list. You can choose to use either KDM or GDM, you can not start GDM from KDM.

- Frode[/QUOTE]
 Is it absolutely not possible to choose KDM or GDM as when I require just before log-in?

It would better if so possible...

---

### Post by Seth on 2005-04-22
I don't understand. You can access KDE and Gnome from either display manager.

---

### Post by Cool_dude_Prav on 2005-04-22
[QUOTE=Seth]I don't understand. You can access KDE and Gnome from either display manager.[/QUOTE]
 What I mean is that instead of first loggin into KDE(say my default) and then choosing GDE and then logging out and again logging into GDE, I say is too much of a hassle...

Is it possible that each time i login, i can choose which DE i want to use?

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=Cool_dude_Prav]What I mean is that instead of first loggin into KDE(say my default) and then choosing GDE and then logging out and again logging into GDE, I say is too much of a hassle...

Is it possible that each time i login, i can choose which DE i want to use?[/QUOTE]
 Yes. At login screen (both GDM and KDM), there is "session" button. SO you can login to GNOME from KDM, and you can login to KDE from GDM.

Again: *DM is the login manager - program  responsible for creating login screen and nothing else.

---

### Post by siebzehn on 2005-04-22
[QUOTE=Alexander Kirillov]Yes. At login screen (both GDM and KDM), there is "session" button. SO you can login to GNOME from KDM, and you can login to KDE from GDM.

Again: *DM is the login manager - program  responsible for creating login screen and nothing else.[/QUOTE]
 Just remember that you won't see a KDE session login in GDM unless you already installed kde ;)

In some distros GNOME and KDE are installed by default, not in UBUNTU

---

