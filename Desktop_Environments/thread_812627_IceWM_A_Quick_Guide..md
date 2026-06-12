---
title: "IceWM: A Quick Guide."
date: 2008-05-30
forum: Desktop Environments
---

### Post by Mark76 on 2008-05-30
I've been using iceWM for less than a day now. It's fast, looks good (loads of themes available even before you start adding them from [www.box-look.org](www.box-look.org)) and is very easy to tweak to your requirements.  What follows is a short tutorial for customising IceWM.

**_1: Autostart_**

Okay, so you've installed iceWM and logged into it. Now you want some applications to launch on start up (update-notifier springs to mind). Easy peasy :). SImply open the file manager (look in the menu or open it from a terminal), go to your home folder, click on the .icewm (if you don't already know this a "." in front of a folder or file name indicates that it is hidden; so you'll need to enable "view hidden" in your file manager's view menu) and add a file called startup.  Open the new file with your favourite text editor and add entries for each application you want autostarted, thus:

> pidgin&
firefox&
(sleep 2; psi&)&
rhythmbox&
(sleep 4; psi&)&
update-notifier&
(sleep 6; psi&)%

(Note: the sleep is just to make sure everything doesn't try to open at the same time).

Now when you log out and log in again all the applications you added to your startup file will run automatically. Neat :D

**_2: Adding launchers to the toolbar_**

Popup/dropdowm menus are all well and good, but some applications we want to be able to get to without having to go through a bunch of menus and submenus. The iceWM toolbar already has launchers for the terminal and browser, but what about your file manager? Or even a screenshot app for those moments when you feel especially chuffed with a new desktop configuration?  Well, fear not, because adding new launchers to the toolbar is as easy as a-b-c.

So let's do it.

A: Open your file manager and navigate to /etc/X11/icewm.  In here you'll find a file called "toolbar" Copy it and place it in the .icewm folder in your home directory.

B: Open the copy and add a line for each app you want on the toolbar in this format

prog  "application name" (for the tooltip) /usr/share/pixmpas/app-icon.png (for the icon. Note it has to be png or something other than svg. Also note that you can use icons from any folder as long as they're not svgs) application (executable)

So thats...

prog "application name" /usr/share/pixmaps/app-icon.png application

C: Close and save the editor, then if everything went to plan the new launchers should appear on the toolbar at the next login at the very least.

**_3: Setting a background_**

Some iceWM themes come with their own default wallpaper; and some don't. Regardless you might prefer to set your own.  Although it's not *quite* as straightforward as opening a gui desktop preferences application, it's not terribly complicated either.  To find the preferences file go to /usr/share/icewm. Once there copy it and place it in the .icewm folder in your home folder (or /etc/X11/icewm if you don't mind running as root for a bit).

Open the copy with your favourite text editor and scroll down right to the bottom. Here you'l find this

> #  Desktop background image
# DesktopBackgroundImage=""

To get iceWM to set a background image just uncomment the second line and then add the path to your chosen image between the quotation marks. You can also set a background colour if you prefer as well as several other options.  Note, I installed gsetroot before I discovered this; so I'm not sure if I can do this because of that or regardless of it.  Try it without gsetroot first and if nothing happens just install that and add your background image to it.

You can have desktop icons with idesk, but I really don't feel the need to explore that. :)

---

### Post by Mark76 on 2008-05-30
Because everyone loves them, here are a couple of screenshots

Note, I'm using the Dusk theme.

---

