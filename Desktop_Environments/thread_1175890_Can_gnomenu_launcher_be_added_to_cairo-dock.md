---
title: "Can gnomenu launcher be added to cairo-dock?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by upptown on 2009-06-01
Done several google searches and forum searches but haven't seen any info on launching gnomenu from cairo-dock.  Any ideas?

---

### Post by fabounet on 2009-06-02
did you try the GMenu applet ? it puts the Applications Menu into your dock.
dunno if it's what you want.

---

### Post by Feelin_froggy8877 on 2009-06-02
its in the desktop section of cario-dock settings

---

### Post by Cuco3 on 2009-12-07
I think he meant GnoMenu, not GMenu. I'm also looking for a way to replace GMenu with GnoMenu in cairo-dock if anybody knows how.

---

### Post by Whise on 2009-12-07
since version 2.1 GnoMenu can be launched from cairo-dock, just make shure you enable cairo-dock's dbus plugin

---

### Post by fabounet on 2009-12-07
could you please provide a way to do this ?
It could be interesting for many people I think.
Thanks !

---

### Post by Whise on 2009-12-08
just install GnoMenu (version 2.1), then just go to cairo/dock preferences, activate the dbus plugin, restart cairo dock, go to the preferences again and gnomenu will be in the desklets section

---

### Post by fabounet on 2009-12-08
oh ok, nice, I didn't know they made an external applet for the dock !
thanks for the tip and thanks to them ^_^

---

### Post by Whise on 2009-12-08
since im the lead developer of gnomenu , i thank you for your thanks )

---

### Post by Cuco3 on 2009-12-14
Whise: I'm using Gnomenu 2.1 but can't seem to find where the setting is for Gnomenu in Cairo.

Here's what I do.

1. Enabled D-Bus in Cairo.
2. Restart Cairo.
3. Go To Cairo-Dock > Configure
4. Go to Appearance > Desklets

but there's nothing there for Gnomenu. Am I missing something? I'm using Cairo-Dock 2.1.2-1

I've looked all around Cairo-Dock, even filtered using the string "gno", and nothing appears for gnomenu.

Thanks for your help and for helping make Gnomenu.

---

### Post by fabounet on 2009-12-14
the "Deslkets" lets you configure the appearance of desklets.
Here the Gnomenu applet is probably in another category, like Accessories, Desktop or Controllers.

---

### Post by Cuco3 on 2009-12-14
> **fabounet said:**
> the "Deslkets" lets you configure the appearance of desklets.
Here the Gnomenu applet is probably in another category, like Accessories, Desktop or Controllers.I've looked around everywhere in Cairo-Dock, even filtered using the string "gno", but nothing for Gnomenu appears.

---

### Post by Whise on 2009-12-14
step by step.

Install GnoMenu version > 2.1

Start Cairo dock
Open cairo dock preferences
Goto Plugins
Enable Dbus Plugin
Restart Cairo Dock
GnoMenu should be visible in the desklet section
If not make shure the dbus plugin is enabled (sometimes it screws up)

---

### Post by Cuco3 on 2009-12-14
I followed your instructions to the tee, Whise, but nothing. I appreciate your help, though.

Maybe I should file a bug report or wait for a new version to come out? I'm pretty sure this has something to do with Cairo-Dock and the DBus plug in rather than Gnomenu. I wish there were other DBus programs that I could test out to make sure that's the culprit.

---

### Post by Cuco3 on 2009-12-14
I even went an added the Cairo-Dock team's PPA to my Software Sources, got the latest Cairo-Dock (2.1.2-4), but no results.
[]("http://www.youtube.com/watch_private?v=JsywEwYAnb0&sharing_token=902XJQTgzHXdFDPhOYjE7Q==")

---

### Post by gkantun on 2009-12-14
Here is my workaround:
[LIST=1]
[*] Download the files GnoMenu, GnoMenu.conf and icon from
[http://bazaar.launchpad.net/~gnomenu-team/gnomenu/trunk/files/203/src/share/cairo-dock/third-party/GnoMenu/](http://bazaar.launchpad.net/~gnomenu-team/gnomenu/trunk/files/203/src/share/cairo-dock/third-party/GnoMenu/)

[*] In 
~/.config/cairo-dock/
create a folder named third-party

[*] In 
~/.config/cairo-dock/third-party
create a folder named GnoMenu

[*] Copy the three downloaded files to
~/.config/cairo-dock/third-party/GnoMenu

[*] Don't forget to set the appropiate permissions to the file GnoMenu.

[*] Execute in the terminal
```
cd ~/.config/cairo-dock/third-party/GnoMenu
./GnoMenu

```
[/LIST]

The GnoMenu item should appear in the Accessories section of the preferences.

---

### Post by Cuco3 on 2009-12-14
> **gkantun said:**
> Here is my workaround:
[LIST=1]
[*] Download the files GnoMenu, GnoMenu.conf and icon from
[http://bazaar.launchpad.net/~gnomenu-team/gnomenu/trunk/files/203/src/share/cairo-dock/third-party/GnoMenu/]("http://bazaar.launchpad.net/%7Egnomenu-team/gnomenu/trunk/files/203/src/share/cairo-dock/third-party/GnoMenu/")
[*] In 
~/.config/cairo-dock/
create a folder named third-party
[*] In 
~/.config/cairo-dock/third-party
create a folder named GnoMenu
[*] Copy the three downloaded files to
~/.config/cairo-dock/third-party/GnoMenu
[*] Don't forget to set the appropiate permissions to the file GnoMenu.
[*] Execute in the terminal
```
cd ~/.config/cairo-dock/third-party/GnoMenu
./GnoMenu

```
[/LIST]

The GnoMenu item should appear in the Accessories section of the preferences.Thanks, but what are the appropriate permissions? Here's what I have;

```
drwxr-xr-x 2 alex alex 4096 2009-12-14 19:04 GnoMenu
```Those permissions are recursive throughout the GnoMenu folder
[COLOR=Red][B]
***edit***[/B][/COLOR] OK, got it to work. Thanks.

Only two weird things:
1) when you click the GnoMenu icon, the menu appears in the middle. 
2) when Cairo-Dock is restarted, the GnoMenu is gone. I have to go to the Cairo-Dock preferences and re-enable it.

If it's of any use, here's the output of ./GnoMenu
```
>>> registering our applet...
Traceback (most recent call last):
  File "./GnoMenu", line 303, in <module>
    applet_share_data_dir)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.GLib.UnmappedError.GTypePrivateGTypeFlags.Code1: applet GnoMenu has been registered, but is not wanted by the user.
```

---

### Post by gkantun on 2009-12-14
Executing permissions.
```
-rwxr-xr-x 1 kantun kantun 9445 2009-12-14 17:13 GnoMenu
```

---

### Post by Cuco3 on 2009-12-14
> **gkantun said:**
> Executing permissions.
```
-rwxr-xr-x 1 kantun kantun 9445 2009-12-14 17:13 GnoMenu
```Yeah, that's what I got.

Does your menu appear in the middle when you click the GnoMenu icon?

And do you have to restart the GnoMenu everytime you close Cairo?

---

### Post by gkantun on 2009-12-14
Maybe you need to set writing permission for the file GnoMenu.conf, "when I restarted, the GnoMenu was still there".

By the way, the menu appears in the middle.

---

### Post by Cuco3 on 2009-12-15
> **gkantun said:**
> Maybe you need to set writing permission for the file GnoMenu.conf, "when I restarted, the GnoMenu was still there".Here are my permissions. Gonna try changing it to 777 to see if that works.> ls -l .config/cairo-dock/third-party/GnoMenu/
total 20
-rwxr-xr-x 1 alex alex 9445 2009-12-14 19:04 GnoMenu
-rwxr-xr-x 1 alex alex 2705 2009-12-14 19:03 GnoMenu.conf
-rwxr-xr-x 1 alex alex 3454 2009-12-14 19:04 icon[COLOR=Red]***edit***[/COLOR] tried it out, but nothing. It's ok, GnoMenu stays on after logoff/shutdown; it's only when I manually close Cairo-Dock that Gnomenu has to be re-enabled. > **gkantun said:**
>  By the way, the menu appears in the middle.Maybe in the future they'll have it so it stays on top of the Gnomenu icon. Not complaining though, I love Gnomenu! 

Thanks for everyone's help. I appreciate it.

---

### Post by Whise on 2009-12-15
its opens in the middle because i dont know how i can find the applet position in the dock, so i set it to the middle, if someone knows how to get the applet x please let me know

---

### Post by fabounet on 2009-12-15
isn't it possible to just pop-up on the mouse ?
because when you click on the launcher, the mouse is on it, so if you know the mouse position on the screen, you know the icon's position ;-)

---

### Post by Whise on 2009-12-15
its not possible yet because i cannot access the applet window, since gnomenu applet and gnomenu window run independently (this is good because it allows me to create applets for other docks, panels easily) i cannot access mouse position without the applet window (in orther to get that mouse event), however im working on it, any input on this would be nice)

Example: 
In awn i can get events for the applet window therefore i can get mouse events, but in awn i dont need that because awnlib also provides applet position
In cairo dock everything is done thought dbus, that way i get a limited ammount of information, however since i dont know all cairo-dock dbus calls i may be missing something

---

### Post by fabounet on 2009-12-16
I think it's possible to know the position of the mouse on the root window (independantly of your window, or even if you don't have any window)
which would solve your problem. :-)

---

### Post by Whise on 2009-12-16
yes, thats the alternative im considering, im not shure if its going to work as expected though, thanks for your input

---

### Post by fabounet on 2009-12-17
you can use for instance ```

gdk_display_get_pointer (GdkDisplay *display,
                        GdkScreen **screen,
                        gint *x,
                        gint *y,                                                                                               GdkModifierType *mask
);

```

and then pop-up the menu on (x,y)

---

### Post by Whise on 2009-12-18
Cairo dock instalation has been fixed in gnomenu 2.2.1 , also now it centers on your mouse click :)

---

### Post by Cuco3 on 2009-12-18
Thanks, Whise!

I tried doing "sudo apt-get update && sudo apt-get upgrade" but the new gnomenu doesn't install. I double checked my software sources and the PPA for Gnomenu is there. I'm currently using Gnomenu 2.1

Anybody else having the same problem?

I'd rather go through aptitude rather than downloading the source and compiling it.

---

### Post by Whise on 2009-12-19
the pppa needs updating , there is a gnomenu package in getdeb , however i advise you to wait for 2.2.2 that is currently behing uploaded because 2.2.1 has a bug, or install the tarball that is very simple

---

### Post by Cuco3 on 2009-12-19
I double checked my sources.list with the PPA on the Gnomenu-Team site, and both are identical. :confused: or did you mean it needs updating on the Gnomenu-Team's end? I'm guessing the latter.

**[COLOR=Red]*edit*[/COLOR]** I updated via source and it went smooth. I know you're busy, but I'll just mention that Gnomenu still displays the menu in the middle. I'm gonna try gkantun's method for manually installing the menu into Cairo-Dock to see if that fixes it.

On a side note, it seems you fixed the flickering images when navigating the gnomenu, which is a huge plus!

**[COLOR=Blue]*edit*[/COLOR]** running gkantun's fix works! GnoMenu 2.2.2 is awesome.

---

### Post by Cuco3 on 2009-12-19
Anyone know of a way to change the text color of the menu? For example, in the Glass theme, the menu fonts are black, which makes it impossible to read what the text that's on the glass part if using a non-white wallpaper.

nevermind, just noticed that you can go to /usr/share/gnomenu/Themes/menu then pick a theme folder, switch to it, and edit it's "themedata.xml" using sudo nano.

---

### Post by fabounet on 2010-01-12
Hi,
I had to make some changes to the DBus API, to optimize the loading of the external applets.
I'm afraid it has somewhat broken the way applets are loaded into the dock.
The changes are effective from Cairo-Dock 2.1.3, which is currently in the release process.

Since I'm faulty here, I've rewritten the GnoMenu applet to make it compliant with the new version of CD (and at the same time, I've cleant te code too)
Here are the complete files, hope this reduces the disturbance ^_^
[tarball]("http://dl.free.fr/tpcZGEpsB")

---

### Post by Cuco3 on 2010-01-18
The option for Gnomenu doesn't appear in the Cairo-Dock configuration and, needless to say, Gnomenu doesn't work for Cairo-Dock any more. :(

This refers to the new Cairo-Dock update version 2.1.3.
> **fabounet said:**
> Hi,
I had to make some changes to the DBus API, to optimize the loading of the external applets.
I'm afraid it has somewhat broken the way applets are loaded into the dock.
The changes are effective from Cairo-Dock 2.1.3, which is currently in the release process.

Since I'm faulty here, I've rewritten the GnoMenu applet to make it compliant with the new version of CD (and at the same time, I've cleant te code too)
Here are the complete files, hope this reduces the disturbance ^_^
[tarball]("http://dl.free.fr/tpcZGEpsB")What should we do with the files inside here?

---

### Post by fabounet on 2010-01-18
just extract them into ~/.config/cairo-dock/third-party
(create the folder if it doesn't exist yet).

then restart the DBus applet, and reopen the config panel to activate the Gnomenu applet.

---

### Post by Cuco3 on 2010-01-21
Hmm... I did as you said (copy GnoMenu folder to ~/.config/cairo-dock/third-party , restart DBus, close-open cairo-dock control panel) but GnoMenu doesn't work. The icon appears in Cairo-Dock control panel and in the dock, but when I click on the GnoMenu icon, nothing happens. I even closed Cairo-Dock.

---

### Post by fabounet on 2010-01-21
it does work for me (the first launch of Gnomenu takes few seconds though, I guess it has to load its stuff)

Here is what I get in the terminal when I click on the icon
```
cd_dbus_applet_emit_on_click_icon (GnoMenu, 272)
emit clic on main icon
cd_dbus_applet_get (x)
cd_dbus_applet_get (y)
x, y, orient: 1228 977 0
show

```

---

### Post by Cuco3 on 2010-01-22
Nevermind I just followed gkantun's advice (again). Pretty funny this guy knows the program better than the programmers. ;)

---

### Post by rahilm on 2010-01-26
i have a dumb question.how to enable the dbus plugin?, because i don't seem to have it..

---

### Post by fabounet on 2010-01-26
it's in the "plug-ins" section of the config panel (at the bottom)

---

### Post by rahilm on 2010-01-26
> **fabounet said:**
> it's in the "plug-ins" section of the config panel (at the bottom)
here's  a screenshot of my config panel i don't see any dbus

---

### Post by fabounet on 2010-01-26
indeed, you also don't have the Switcher
I guess this is an old version (the one in the Ubuntu repository ?)
you need 2.1.3 go get external applets like Gnomenu.

---

### Post by rahilm on 2010-01-26
hurrayy!!!
i've installed the latest cairo-dock from the ppa and it is working like charm..
except from the fact that whenever i start cairo-dock , the computer logouts automatically and that i cannot start vlc anymore..
wow what a dock!!

---

### Post by rahilm on 2010-01-26
i am now using indriect rendering mode. it is working. but when i do ./GnoMenu as explained in the tutorial i get:
```

>>> registering our applet...
Traceback (most recent call last):
  File ".config/cairo-dock/third-party/GnoMenu/GnoMenu", line 303, in <module>
    applet_share_data_dir)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "RegisterNewModule" with signature "ssssis" on interface "org.cairodock.CairoDock" doesn't exist

```

---

### Post by fabounet on 2010-01-27
you don't have to do anything, the dock will do it for you !
just extract my tarball to the third-party folder, then deactivate/reactivate the DBus applet to make it reload the external applets, then re-open the config panel, you will see the new applet there. Activate it, and you're done :)

PS : what tutorial are you talking about ? it's probably outdated with the new version.

---

### Post by rahilm on 2010-01-27
thanks...its working now
but i have to add it everytime i start the dock!

---

### Post by fabounet on 2010-01-27
yep, it has been fixed 2 days ago :D
the weelky package already contains the fix.

---

### Post by rahilm on 2010-01-27
how do i change the icon on dock to that of the button icon of gnomenu?

---

### Post by fabounet on 2010-01-28
you can do that like for any launcher/applet, right click on it -> configure this applet

---

### Post by xx58 on 2010-01-28
:rolleyes: Good

---

### Post by rahilm on 2010-01-28
> **fabounet said:**
> you can do that like for any launcher/applet, right click on it -> configure this applet
i mean the button icons used in the themes...on gnome-look.org

---

### Post by oakgrove on 2010-02-05
I'm not sure what I'm doing wrong.  I have Cairo-dock version 2.1.3-1 and Gnomenu version 2.3.  I copied the three files, GnoMenu, GnoMenu.conf and icon from
[http://bazaar.launchpad.net/~gnomenu...party/GnoMenu/](http://bazaar.launchpad.net/~gnomenu...party/GnoMenu/), placed them in ~/.config/cairo-dock/third-party/GnoMenu, and chmodded GnoMenu +x.  I then made sure that dbus was checked in my cairo-dock settings and even made sure all of the options were checked inside of that.  I restarted cairo-dock multiple times, restarted the computer, and Gnomenu is never even in my settings anywhere.  When I try to run the Gnomenu command in my config directory, I get:
```

nate@e8400:~/.config/cairo-dock/third-party/GnoMenu$ ./GnoMenu
>>> registering our applet...
Traceback (most recent call last):
  File "./GnoMenu", line 303, in <module>
    applet_share_data_dir)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "RegisterNewModule" with signature "ssssis" on interface "org.cairodock.CairoDock" doesn't exist

```
I know that Gnomenu works because I can add it to gnome-panel, run it from the tray, etc. and it works fine.  I tried searching for gnomenu with the "filter" in cairo-dock to no avail so I know it isn't there.

Where am I messing up?

---

### Post by fabounet on 2010-02-06
I think you need Gnomenu 2.4

---

### Post by oakgrove on 2010-02-06
> **fabounet said:**
> I think you need Gnomenu 2.4

Excellent.  Works like a charm now.  Thanks.

---

### Post by KernelKnight on 2010-03-25
Sorry to revive an old thread, but I have both the newest version of cairo-dock and GnoMenu, and I have followed the instructions, but it still does not show up. What permissions apart from a+x should I add to the GnoMenu file? I get the same message as oakgrove when I run the command.

[edit]
Nevermind. I got it.

---

