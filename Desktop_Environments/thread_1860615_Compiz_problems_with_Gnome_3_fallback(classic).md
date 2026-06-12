---
title: "Compiz problems with Gnome 3 fallback(classic)"
date: 2011-10-14
forum: Desktop Environments
---

### Post by drjaydub on 2011-10-14
](*,)I have installed compiz on ubuntu 11.10 that has gnome shell and fallback installed.  When i use compiz setting managers and check the plugins the plugins do not take affect.  When i typed "compiz --replace" finally the plugins took affect and it worked:).  As i log out and log back in my compiz settings were not saved:( therefore effects werent there.  any solutions?...thanks...really want my flaming windows and cube back :D...and i dont want to use lxde or xcfe desktop

---

### Post by drjaydub on 2011-10-14
btw i want to use gnome fallback/classic with the compiz effects..just making sure if i wasnt clear enough

---

### Post by Krytarik on 2011-10-15
This should lead to Compiz being run automatically in the "GNOME Classic" session:

[LIST=1]
[*]Install "gconf-editor" if it isn't already.
[*]Open it.
[*]Find the key "/desktop/gnome/session/required_components/windowmanager", and set it to "compiz".
[*]Relogin.
[/LIST]
Regards.

---

### Post by skullriot on 2011-10-15
I'm having the same problem, but the thread stops at desktop. There is no session folder and the subsequent items obviously cant be found. Even if i run gconf-editor as sudo, the options aren't there.

---

### Post by Krytarik on 2011-10-15
> **skullriot said:**
> I'm having the same problem, but the thread stops at desktop. There is no session folder and the subsequent items obviously cant be found. Even if i run gconf-editor as sudo, the options aren't there.
Ok, then it seems that - regardless of ["gnome-wm"s man page]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/gnome-wm.1.html") - those settings keys have been moved to DConf as well, as quite a lot of other settings, too.

So, please install the package "dconf-tools", if it isn't already, and search in "dconf-editor" instead, also named "Configuration Editor", the same as "gconf-editor"; don't mix them. :p

As I don't have an Oneiric system at hand right now, I can't say exactly where you'll find those settings keys, but I'd start searching under "desktop", obviously. :D

Please report back where you've found them! Thanks!

---

### Post by skullriot on 2011-10-15
I found something in dconf-editor

/org/gnome/desktop/session

and the options in that selection are idle-delay and session-name. Should i change session-name from gnome to compiz? Side question, would the auto login to the fallback DE be in this area as well?

---

### Post by Krytarik on 2011-10-15
> **skullriot said:**
> Even if i run gconf-editor as sudo, the options aren't there.First, I forgot to mention that you shouldn't run "gconf-editor", or "dconf-editor", for that matter, as root! As otherwise, you'd see/change root's settings, not yours!

Moreover, don't use "sudo" for running graphical apps as root, use "gksudo" instead. See here why:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **skullriot said:**
> I found something in dconf-editor

/org/gnome/desktop/session

and the options in that selection are idle-delay and session-name. Should i change session-name from gnome to compiz?Nope, don't do that! Search further, it must be somewhere. :P

> **skullriot said:**
> Side question, would the auto login to the fallback DE be in this area as well?
You mean, setting the display manager - presumably LightDM in your case - to 1) automatically log you in 2) to the "GNOME Classic" session?
For both settings, please see this guide:

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

If you are not using LightDM, but GDM, you should find "Login Screen" somewhere in the menus, but I don't exactly where it is now, as the "System" menu is removed now. Maybe under your name on the right side of the panel. Otherwise, you could just run "gdmsetup" from the Terminal or the Alt+F2 dialog. :P

---

### Post by skullriot on 2011-10-15
Thanks for the auto login link. 

I cant find any window manager options in dconf. Would there be a config file somewhere i could sudo gedit? Thanks for your help so far. Maybe i should note, this is a fresh install, i had problems when i upgraded from natty, ubuntu would get stuck in dos while loading some pulse audio thing. That wouldnt be affecting this would it? I did a wipe and install. Also, im trying to do this from the fallback environment.

---

### Post by Krytarik on 2011-10-15
> **skullriot said:**
> I cant find any window manager options in dconf. Would there be a config file somewhere i could sudo gedit?
Too bad. Would have been the easiest way. However, there are 2 other options that come into play now:

a) Second-best method, as it wouldn't change settings system-wide, but only for your user.

Copy "/usr/share/applications/gnome-wm.desktop" into your "~/.local/share/applications", and change its value for "Exec" to "compiz", like this:
```
[Desktop Entry]
Type=Application
Name=Window Manager
Exec=[COLOR=Red]**compiz**[/COLOR]
NoDisplay=true
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
X-GNOME-Autostart-Notify=true
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```b) Brute-force method; this would change the session settings of "GNOME Classic" system-wide. And it would also be reverted by an upgrade of the package "gnome-session-fallback".

Open "GNOME Classic"s session settings:
```
gksudo gedit /usr/share/gnome-session/sessions/gnome-classic.session
```Change "gnome-wm" in it to "compiz", like this:
```
[GNOME Session]
Name=GNOME Classic
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;notifications;
DefaultProvider-windowmanager=[COLOR=Red]**compiz**[/COLOR]
DefaultProvider-notifications=notify-osd
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
DesktopName=GNOME
```> **skullriot said:**
> Maybe i should note, this is a fresh install, i had problems when i upgraded from natty, ubuntu would get stuck in dos while loading some pulse audio thing. That wouldnt be affecting this would it?
Nope, not at all.

---

### Post by skullriot on 2011-10-15
Hrm. Those arent working. I can force compiz to load, but it's doing crazy stuff for about a minute before it loads in right. I would prefer not having to add the script to my boot menu.

For method a) The file wasn't there. Whether i sudo'ed or not, it just didnt show up. maybe thats my problem?

Method b) The file is there, i can edit it and it saved, and after a reboot the revision is still there, however it seems to not want to load compiz. 

I don't know much, but what i do know is that it seems to be something between loading gnome fallback and whatever else is loaded.

---

### Post by Krytarik on 2011-10-15
> **skullriot said:**
> For method a) The file wasn't there. Whether i sudo'ed or not, it just didnt show up. maybe thats my problem?
This file should be definitely there, as it's part of the package that provides you the very session you are trying to tweak, "[gnome-session-fallback]("http://packages.ubuntu.com/oneiric/all/gnome-session-fallback/filelist")", which also includes the file you *have* found.

So, I guess, you just didn't *see* it, as .desktop files are handled differently from usual files; if you open the stated directory in Nautilus, you will see their names displayed as the value of the "Name" entry included in them, in this case "Window Manager". Moreover, by default you can't just use the context menu to 1) rename them (this would change the value of its "Name" entry instead), and 2) open them for editing. Instead, you need to open them from within the Text Editor. So, more precisely, it's now:

[LIST=1]
[*]Find "Window Manager" in "/usr/share/applications".
[*]Copy it into your "~/.local/share/applications".
[*]Open the Text Editor.
[*]Open "~/.local/share/applications/gnome-wm.desktop" from within it.
[*]Change "gnome-wm" to "compiz".
[*]Save it, quit.
[/LIST]
Btw., the same is true for "index.theme" files of themes and icon themes.

> **skullriot said:**
> Method b) The file is there, i can edit it and it saved, and after a reboot the revision is still there, however it seems to not want to load compiz.
This should work if Compiz doesn't crash for some reason upon running it at login, which is indicated by this:
> **skullriot said:**
> I can force compiz to load, but it's doing  crazy stuff for about a minute before it loads in right.
So, the question is now why Compiz behaves that way at your system.

Do you have the best available driver for your video card/chip installed?
How about "Additional Drivers", if you have an Nvidia or non-legacy AMD/ATI card/chip?

---

### Post by JayD239 on 2011-10-15
I also want to do this. 

I have no key [FONT="Courier New"]/desktop/gnome/session/required_components/windowmanager[/FONT] in my gconf or something similar in dconf.

I have an existing gconf key [FONT="Courier New"]/desktop/gnome/applications/window_manager[/FONT] with current and default set on compiz ([FONT="Courier New"]/usr/bin/compiz[/FONT])

I have also tried adding an update-alternative like this: [http://wiki.debianforum.de/Compiz_-_OpenGL_Fenster-_und_Compositingmanager](http://wiki.debianforum.de/Compiz_-_OpenGL_Fenster-_und_Compositingmanager)

But alas, still forced to use [FONT="Courier New"]compiz --replace[/FONT]

-- quick edit

Aha, i just found your bruteforcing method. I glad i did, that did work! Although i had to edit the gnome-fallback.session instead of the gnome-classic like you mentioned

---

### Post by Krytarik on 2011-10-15
> **JayD239 said:**
> Aha, i just found your bruteforcing method. I glad i did, that did work! Although i had to edit the gnome-fallback.session instead of the gnome-classic like you mentioned
Are you using the "GNOME Classic" session, on which I built my instructions; or "GNOME Classic (No effects)", which would be kinda funny actually, to run Compiz in those. :P

---

### Post by glennric on 2011-10-16
I am having this problem too. The problem is that the gnome-classic session fallback is being called.  The fallback of course is the gnome-fallback session (which is what you get if you select GNOME Classic (No effects) from the login).  For some reason the GNOME Classic (gnome-classic) session is failing to load.  I have not figured out how to work around this yet.

---

### Post by glennric on 2011-10-16
I know this is off topic, but does anyone else have the problem with the GNOME Classic session that the alt-right click on the gnome panel does not work once compiz is running?  I have this issue and it is rather annoying.

---

### Post by Krytarik on 2011-10-16
> **glennric said:**
> The problem is that the gnome-classic session fallback is being called.  The fallback of course is the gnome-fallback session (which is what you get if you select GNOME Classic (No effects) from the login).  For some reason the GNOME Classic (gnome-classic) session is failing to load.
Yeah, exactly; I've just got the same idea, assuming that "GNOME Classic (No effects)" isn't actually chosen at the login screen.

So, let's have a look at the session settings again:
```
[GNOME Session]
Name=GNOME Classic
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;notifications;
DefaultProvider-windowmanager=compiz
DefaultProvider-notifications=notify-osd
**IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated**
FallbackSession=gnome-fallback
DesktopName=GNOME
```You see that "/usr/lib/gnome-session/gnome-session-check-accelerated" is run to check if ...well, it's pretty much self-explanatory, eh!? ;-)

Just try running it yourself in a Terminal, to see if it outputs an info similar to those of the Unity/Compiz support checks. And no, I didn't find a man page on this.

---

### Post by JayD239 on 2011-10-16
> **Krytarik said:**
> Are you using the "GNOME Classic" session, on which I built my instructions; or "GNOME Classic (No effects)", which would be kinda funny actually, to run Compiz in those. :P

I am running the "GNOME Classic", not the No effects one.

> **glennric said:**
> I know this is off topic, but does anyone else have the problem with the GNOME Classic session that the alt-right click on the gnome panel does not work once compiz is running?  I have this issue and it is rather annoying.

Yes, this is also happening to me

> **Krytarik said:**
> Just try running it yourself in a Terminal, to see if it outputs an info similar to those of the Unity/Compiz support checks. And no, I didn't find a man page on this.

This command does not output anything for me. I'm using an ATI RV730XT [Radeon HD 4670] with the 11.4 fglrx driver, which is perfectly capable to run an accelerated desktop

---

### Post by glennric on 2011-10-16
Krytarik:  The problem is not with the IsRunnableHelper.  That runs fine an gives a return value of 0 (i.e. everything is good).  Also, if you remove the IsRunnableHelper and the FallbackSession from the gnome-classic.session then all that happens when you try to log into the session a dialog pops up telling you that the session failed.

To put it simply for you, the gnome classic session is not working as it should be.  The Ubuntu devs have focused on the switch to the Unity/Gnome desktop and have for the most part ignored issues with the classic desktop.  The end result is that the classic session is buggy and poorly setup, while at the same time the unity session is buggy and poorly setup because it is not ready yet.  Leaving Ubuntu a real mess.  If this happened for one of the projects that I develop for I would be rather embarrassed.

Okay, so while ranting above I was also working on this issue.  I found the problem and a work around.  Change line 3 of the file /usr/share/gnome-session/sessions/gnome-classic.session from
"RequiredProviders=windowmanager;notifications;"
to
"RequiredProviders=windowmanager;"
With that change gnome classic session succeeds to start and compiz is running.  So the notifications thing is not working.

---

### Post by glennric on 2011-10-16
By the way, as to my comment about the alt-right-click issue with the gnome-panel earlier, I discovered that if you hold down alt, then hold down the left mouse button, then hold down the right mouse button, then the context menu opens.  Annoying, but it is a workaround.

---

### Post by skullriot on 2011-10-16
Thanks Krytarik and glennric, you have fixed my system! It was the notifications that was preventing things from running right. Also, the alt-right click workaround is working for me as well. I do agree that there should have at least been a 100% DE left behind before moving on to a new DE. Thanks for the help though, you affirm my faith in the ubuntu community.

---

### Post by Krytarik on 2011-10-16
I've just compiled a comprehensive guide about the whole matter :D :

[http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html](http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html)

Regards.

---

### Post by opodaniel on 2011-10-17
**:~$ cat /usr/share/gnome-session/sessions/gnome-classic.session **
> [GNOME Session]
Name=GNOME Classic
RequiredComponents=gnome-panel;gnome-settings-daemon;
#RequiredProviders=windowmanager;notifications;
RequiredProviders=windowmanager;
#DefaultProvider-windowmanager=gnome-wm
DefaultProvider-windowmanager=compiz
DefaultProvider-notifications=notify-osd
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
DesktopName=GNOME
it doesn't start for me using this settings. I am happy for having compiz effects back anyway, so it is a small victory and thanks for the hacks.

---

### Post by Krytarik on 2011-10-17
> **opodaniel said:**
> it **doesn't start** for me using this settings. I am happy for **having compiz effects back** anyway, so it is a small victory and thanks for the hacks.
Please clarify, as your statement is contradictory.

---

### Post by opodaniel on 2011-10-17
Sorry, my mind was playing on other fields. I was trying to make Conky start, found this post that helped a lot. So what is not starting is conky.
So I was completely off-topic. Your solutions works. thanks a  lot.

---

### Post by skullriot on 2011-10-17
What did you do to make conky start? Im about to mess with setting up conky myself. Or is it one of those things i can just put in the startup options.

---

### Post by skullriot on 2011-10-17
Grar! Ok, since you answerd my question about the auto login thing in this thread, i modified the files and it was working, but now even when i select gnome classic, it still loads unity on top of avant window navigator. I modified the file to make avant load instead of gnome panels. it was working for a bit, but now i dont know what is going wrong.

Edit: NEVERMIND! I logged into ubuntu session and it modified my settings in CCSM.... so i just have to set alternate profiles and change it back. -.-

---

### Post by opodaniel on 2011-10-17
All is ok, i just commented this line on conkymain
**#own_window_type override**
Sorry for the off-topic.

---

### Post by lethalfang on 2011-10-17
I tried this: [http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html](http://www.tuxgarage.com/2011/10/running-gnome-classic-with-compiz.html)

But the compiz/desktop crashes as soon as I tried to use the multiple desktop. Any ideas?

---

### Post by prusswan on 2012-02-06
> **glennric said:**
> By the way, as to my comment about the alt-right-click issue with the gnome-panel earlier, I discovered that if you hold down alt, then hold down the left mouse button, then hold down the right mouse button, then the context menu opens.  Annoying, but it is a workaround.

I have no idea whether to laugh or cry, from right-click it now becomes Alt+LMB+Right click...that's hell of a genius ui improvement :D

---

### Post by LinuXofArabiA on 2012-02-07
Hello Everyone. I just tried running compiz --replace, and everything went haywire! My descktop screen foze and I had to restart my computer. Luckily once I did that, I logged back in and everything was back to normal. Any help or suggestions as to make compiz work properly is appreciated.

Thanks

---

### Post by LinuXofArabiA on 2012-02-07
You know what, dont waste your time. I just found the sticky post in this forum that goes into details about setting up compiz effects.

Thanks

---

### Post by wildmanne39 on 2012-02-07
> **LinuXofArabiA said:**
> You know what, dont waste your time. I just found the sticky post in this forum that goes into details about setting up compiz effects.

ThanksHi, just to clarify the guide in the sticky at the top of this forum is not for gnome 3 fallback.

---

