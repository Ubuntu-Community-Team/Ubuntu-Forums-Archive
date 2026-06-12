---
title: "How do I use KDE or GNOME's login instead of Ubuntu's?"
date: 2007-03-22
forum: Desktop Environments
---

### Post by deadowl on 2007-03-22
I'm trying to customize my system. However, I don't know how to override or remove the Ku/Xu/U/buntu login screen in favor of the default window manager's. Could anyone point me in the right direction?

---

### Post by AtrejuT on 2007-03-22
for gnome: (ubuntu)
under system/administration/login window you can chose which theme to use for the graphical login - I assume thats what you're looking for.
It's on the second tab.

---

### Post by ajgreeny on 2007-03-22
If you mean the splash screen that shows when booting with the moving bar, then it's:-
sudo update-alternatives --config usplash-artwork.so

This will give you a choice of those that are available to you and you can change if you want.

If you mean the kdm or gdm login screen, however, it's
sudo dpkg-reconfigure gdm

If you have gdm, kdm and xdm installed these will be shown as alternatives you can chose from.
I hope this helps.

---

### Post by yigal.weinstein on 2007-03-22
I believe all you have to do is in a terminal (or synaptic etc.)

sudo apt-get install kdm

it will give you the option of choosing itself the KDE desktop manager or keep GDM, which Ubuntu's DM by default.  There is really no advantage in doing this, that I know of, but if you really want it, it is not difficult to do.

---

### Post by deadowl on 2007-03-22
> **yigal.weinstein said:**
> I believe all you have to do is in a terminal (or synaptic etc.)

sudo apt-get install kdm

it will give you the option of choosing itself the KDE desktop manager or keep GDM, which Ubuntu's DM by default.  There is really no advantage in doing this, that I know of, but if you really want it, it is not difficult to do.

Right now I'm primarily using KDE.
I have kdm and gdm installed.
For logging in with gdm as my default session type, the initial screen after what would be usplash is a full-screen with Ubuntu artwork. With kdm as my default session type, the initial screen after what would be usplash is a full-screen with Kubuntu artwork. 

I would like the window manager to handle the login. However, Ubuntu seems to have its own login screen that overrides the ones with kdm and gdm. I have only seen the one for gdm when Ubuntu's login screen crashed (it came up as an alternative).

Also, @ajgreeny, are you sure that's not just for session type?

---

### Post by yigal.weinstein on 2007-03-23
Ok, from what you have told us it seams what you need to do if you already have kdm installed is simply,

sudo dpkg-reconfigure kdm

choose kdm, not gdm which is what you are using right now

log out of KDE, and hit Ctrl+Alt+Del to restart GDM, and after a short time you should be in KDM?

If not post your results

---

### Post by mcduck on 2007-03-23
> **deadowl said:**
> 
I would like the window manager to handle the login. However, Ubuntu seems to have its own login screen that overrides the ones with kdm and gdm. I have only seen the one for gdm when Ubuntu's login screen crashed (it came up as an alternative).

GDM _is_ the login manager of Gnome. If you don't like the Ubuntu theme, use some other. Or if you don't want to use the themeable GDM you can change it to 'plain', which is what you get if the themeable GDM fails. In Gnome, go to System/Administartion/Login Screen and on top of the 'Local'-tab change the Style from 'Themed' to 'Plain'. I suppose this is what you were asking for.

(Window manager manages your windows, it has nothing to do with your login screen, and Ubuntu has not made it's own login manager, just it's own themes for GDM and KDM)

---

### Post by yigal.weinstein on 2007-03-23
Yes, this must be his issue.  One can easily make KDM look like GDM etc..  In fact there is no "GDM" theme or "KDM" theme. 

> **mcduck said:**
> GDM _is_ the login manager of Gnome. If you don't like the Ubuntu theme, use some other. Or if you don't want to use the themeable GDM you can change it to 'plain', which is what you get if the themeable GDM fails. In Gnome, go to System/Administartion/Login Screen and on top of the 'Local'-tab change the Style from 'Themed' to 'Plain'. I suppose this is what you were asking for.

(Window manager manages your windows, it has nothing to do with your login screen, and Ubuntu has not made it's own login manager, just it's own themes for GDM and KDM)

---

### Post by mgmiller on 2007-03-23
I found a really nice blue themed gdm login theme called "Relaxing Water" at gnomelooks.org  It has a watery background and a transparent edged window for the user name and password area.  After you download it, just run System>Administration>Login Window and then click the +add button and navigate to the theme file.  I have changed my Ubuntu to a very blue themed setup and this really adds to the effect.

---

### Post by deadowl on 2007-03-23
Okay, let me tell you:
I AM using kdm.
Telling me to go to something within how your GUI is set up is far from helping me, because my GUI isn't set up that way. Telling me the command I need to run to change a login theme for kdm, if that is my problem, would help.

Login Manager through kcontrol, I've already messed with that; Nothing changes. Is it that I'm looking in the wrong place?

RESOLVED

Was it so hard to say I need to download kdmtheme?

---

### Post by yigal.weinstein on 2007-03-24
Unfortunately it was because we didn't know what you were interested in.  When you say login manager for kde most linux users will say kdm.  When you say change from Ubuntu to KDE again kdm and not necessarily the themes present.  Perhaps a screenshot of what you have and what you want would have helped.  A picture is worth a 1000 words in this case.

> **deadowl said:**
> Okay, let me tell you:
I AM using kdm.
Telling me to go to something within how your GUI is set up is far from helping me, because my GUI isn't set up that way. Telling me the command I need to run to change a login theme for kdm, if that is my problem, would help.

Login Manager through kcontrol, I've already messed with that; Nothing changes. Is it that I'm looking in the wrong place?

RESOLVED

Was it so hard to say I need to download kdmtheme?

---

### Post by everchanging02 on 2007-03-24
> **ajgreeny said:**
> If you mean the splash screen that shows when booting with the moving bar, then it's:-
sudo update-alternatives --config usplash-artwork.so

This will give you a choice of those that are available to you and you can change if you want.

I recently installed kubuntu through my ubuntu (synaptic package manager) and I have the problem that the kubuntu loading screen always runs on startup.  I have used the above command to reset the usplash, but it only sets the shut down screen to my choice, and retains the kubuntu on startup.  I have even gone as far as to delete the usplash-theme-kubuntu.so from my /usr/lib/usplash directory, but it STILL shows the kubuntu splash on startup.
I know it's purely asthetic, but it's rather annoying me.  Any help with this would be great.  Thanks.

 - EC02

---

### Post by deadowl on 2007-03-25
> **everchanging02 said:**
> I recently installed kubuntu through my ubuntu (synaptic package manager) and I have the problem that the kubuntu loading screen always runs on startup.  I have used the above command to reset the usplash, but it only sets the shut down screen to my choice, and retains the kubuntu on startup.  I have even gone as far as to delete the usplash-theme-kubuntu.so from my /usr/lib/usplash directory, but it STILL shows the kubuntu splash on startup.
I know it's purely asthetic, but it's rather annoying me.  Any help with this would be great.  Thanks.

 - EC02

I just removed usplash and let the computer tell me what it's doing.

---

