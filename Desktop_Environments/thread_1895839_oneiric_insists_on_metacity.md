---
title: "oneiric insists on metacity"
date: 2011-12-15
forum: Desktop Environments
---

### Post by Esekla on 2011-12-15
I've used Ubuntu for a long time and have highly customized desktop, using FVWM under a gnome session.  When I upgraded to oneiric, I found that the $WINDOW_MANAGER environment variable was no longer honored.  I had to setup .desktop and .session files for this configuration.  That worked for a while but, after updating software recently, I find that metacity gets loaded by both gnome-session and gnome-session-fallback as the window manager regardless of what I do.  This happens regardless of whether I use gdm, or startx and .xsession from my .profile.  

Here are the related files:  
~$ cat .xsession
/usr/bin/gnome-session-fallback --session=zak  

~$ cat /usr/share/xsessions/zak.desktop
[Desktop Entry] Name=Zak GNOME Comment=This session logs you into GNOME with the traditional panel 
Exec=gnome-session-fallback --session=zak 
TryExec=gnome-session-fallback 
Icon= Type=Application  

~$ cat /usr/share/gnome-session/sessions/zak.session  
[GNOME Session]
Name=Zak GNOME 
RequiredComponents=gnome-panel;gnome-settings-daemon; RequiredProviders=windowmanager;notifications; 
DefaultProvider-windowmanager=fvwm 
DefaultProvider-notifications=notify-osd 
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated 
FallbackSession=gnome-fallback 
DesktopName=GNOME

I'm pretty close to going back to using Debian exclusively as Ubuntu just gets harder and harder to customize.  All I want is for gnome-session to use fvwm as the window manager.

---

### Post by Krytarik on 2011-12-15
Then maybe you shouldn't use executables no other session uses for the initiation. ;-)

This is the content of "/usr/bin/gnome-session-fallback":
```
#! /bin/sh
exec gnome-session --session gnome-fallback "$@"
```And, since it seems like you used the .desktop file of "GNOME Classic", "gnome-classic.desktop", as the template for your session, it seems like you deliberately replaced the correct "gnome-session" command with those! In fact, I'm wondering how it has ever worked, if it was always set up like that.

So set up your session files like this instead:

/usr/share/xsessions/zak.desktop:
```
[Desktop Entry]
Name=Zak GNOME
Comment=This session logs you into GNOME with the traditional panel
Exec=**[COLOR=Red]gnome-session[/COLOR]** --session=zak
TryExec=**[COLOR=Red]gnome-session[/COLOR]**
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```~/.xsession:
```
/usr/bin/[COLOR=Red]**gnome-session**[/COLOR] --session=zak
```You should also have to remove the entry "notifications" from the file below, to make the session actually run, and not fall back again to the "gnome-fallback" session (bug report [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/885939")).

Plus, if your graphics setup doesn't pass the capability check, you need to remove the fallback part outright.

/usr/share/gnome-session/sessions/zak.session:
```
[GNOME Session]
Name=Zak GNOME
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;[COLOR=Red]**notifications;**[/COLOR]
DefaultProvider-windowmanager=fvwm
DefaultProvider-notifications=notify-osd
[COLOR=Blue][B]IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback[/B][/COLOR]
DesktopName=GNOME
```Regards.

---

### Post by Esekla on 2011-12-16
yes fallback was just a later desperation experiment, sorry.

eliminating the notifications seems to be the critical change.

thanks!

---

