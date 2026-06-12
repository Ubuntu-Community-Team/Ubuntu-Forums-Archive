---
title: "How to edit launcher items in unity"
date: 2011-10-22
forum: Desktop Environments
---

### Post by akpraha on 2011-10-22
I installed a custom copy of eclipse by hand (not using the repositories), ran it from a terminal and then used the "keep in launcher" option to add it to the launcher.  It was added as a "question mark" icon, which as an added benefit seemingly does nothing when I click on it.  Looked through /var/log for any error messages, of course there are none.  Looked through the hidden directories in home, no luck there either.

So how do I:
1. Change the icon to something reasonable?
2. Check the configuration of what the launcher is actually launching

It would honestly help if there were some sort of useful documentation on how to configure the launcher, or at least some log files where I could see for myself what is going on.

---

### Post by freddybob on 2011-10-23
I have the same question.

I need to edit a launcher to add start-up parameters to an application.  How do I do this?

As a workaround I would try creating a new launcher but that option seems to have been removed in 11.10.  WTF?

---

### Post by JayKav on 2011-10-23
I just asked a similar question. The answer seems to be to install gnome:

```
sudo apt-get install gnome-session-fallback
```

Logout and then select it before you type your password.

In Gnome, right-click on applications and then edit-menus. At least you can remove the offending item if nothing else.

If you drag the menu item onto the desktop, it adds an entry to the ~/Desktop/alacarte file which shows the application it's trying to run and the location of the icon.

---

### Post by akpraha on 2011-10-24
> **freddybob said:**
> I have the same question.

I need to edit a launcher to add start-up parameters to an application.  How do I do this?

As a workaround I would try creating a new launcher but that option seems to have been removed in 11.10.  WTF?

I did find a workaround.  First create a file with the .desktop extenstion in /usr/share/applications/ .  This will make the application available in the Dash.  For example, my eclipse.desktop looks like:

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
StartupNotify=true
Icon=/opt/eclipse/eclipse-jee-indigo/icon.xpm
Name=Eclipse Indigo
Comment=Programming IDE
Exec=env UBUNTU_MENUPROXY=0 /opt/eclipse/eclipse-jee-indigo/eclipse
Categories=Application;Development;


```

At this point I could locate the program in the dash and at least use the GUI to add it to the launcher.  At least now I have a working launcher for eclipse...

---

### Post by freddybob on 2011-10-24
Thanks, knowing the *.desktop* files were in /usr/share/applications/ was what I needed.

I can now edit a launcher's exec command within its *.desktop* file using gedit:

[FONT="Courier New"]sudo gedit /usr/share/applications/*[application name]*.desktop[/FONT]

---

### Post by Angelus-Michael on 2011-10-24
[COLOR=RoyalBlue]***Did you tried with Startup applications... ?***[/COLOR]

---

### Post by hatredman on 2012-11-23
Sorry to relive such an old topic, and sorry for the cursing.

BUT... I think it's mess not having the ability to edit this kind of thing directly on the launcher icon - right-click on in and edit, for instance. Gnome indeed has shortcomings like this one, but even Gnome is not so annoying. Seems Canonical and the Dev Community want to be Apple. 

It's like being on a plane when you notice an engine on fire. You call the flight-attendant to warn the crew, but she replies "you don't want to know about this. Get back to your seat and watch the movie". Unity is trying to do the same with us.

---

### Post by wildmanne39 on 2012-11-23
Old thread closed.

---

