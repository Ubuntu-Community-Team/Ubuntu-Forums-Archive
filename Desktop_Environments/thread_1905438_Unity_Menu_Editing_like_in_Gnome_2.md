---
title: "Unity Menu Editing like in Gnome 2"
date: 2012-01-06
forum: Desktop Environments
---

### Post by Topazkitty on 2012-01-06
Hi, I have used ubuntu on and off since 10.04 on my laptop and I was wondering if anyone knew of way to edit menu items in Unity like the way it used to be done it the program alacarte. The reason I want to do this is to add flash games into my games menu entry. I have been without a solution since 11.04. Any help would be appreciated.

---

### Post by kimda on 2012-01-07
Adding a shortcut to the sidepanel (launcher) is easy. Open the application you want to add to the sidepanel.. If you go with your mouse to the sidepanel you see the icon. Right click on the icon and select keep in launcher. Now its added to the launcher.

There is no top panel like in Gnome 2. Every program is either started with the launcher or the dash (open dash with windows key or click on the ubuntu logo in the top left corner of the launcher)

---

### Post by Frogs Hair on 2012-01-07
The main menu can be used to do some editing .

---

### Post by Topazkitty on 2012-01-07
Thanks for the suggestions but what I'm looking for is a program that is like Alacarte for unity. I already know how to add launchers to the dock on the side. I also know how to make desktop icons.  

Thanks for ideas but does anyone have any other ones?

---

### Post by jerrrys on 2012-01-07
You can get the gnome2 options (like alacarte) with gnome classic.

open a terminal and enter:

sudo apt-get install gnome-session-fallback

Then log out and log back in in Gnome Classic.

---

### Post by Topazkitty on 2012-01-07
> **jerrrys said:**
> You can get the gnome2 options (like alacarte) with gnome classic.

open a terminal and enter:

sudo apt-get install gnome-session-fallback

Then log out and log back in in Gnome Classic.

That could work but what I really looking for was an alacarte for unity. Should I file another bug report like my previous one for 11.04 that is here.

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/797332](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/797332)

---

### Post by mcduck on 2012-01-08
> **Topazkitty said:**
> Thanks for the suggestions but what I'm looking for is a program that is like Alacarte for unity. I already know how to add launchers to the dock on the side. I also know how to make desktop icons.  

Thanks for ideas but does anyone have any other ones?

The program you are looking for would be...   Alacarte! ;)

Just install it if you haven't done that already, it works just fine with Unity for creating and editing your application launchers. There is no Unity-specific tool for the purpose because there si no reason to have one, Unity uses exactly the same .desktop files and menu structures every other XDG-compatible desktop environment does (and why wouldn't it, you are still running Gnome 3 desktop even with Unity session).

---

### Post by kurt18947 on 2012-01-08
I haven't used used the Unity interface because I prefer Gnome3 shell but I wonder if this would be helpful:
[http://lifehacker.com/5868752/myunity-fixes-annoyances-in-ubuntus-unity-interface](http://lifehacker.com/5868752/myunity-fixes-annoyances-in-ubuntus-unity-interface)

---

### Post by Topazkitty on 2012-01-11
> **mcduck said:**
> The program you are looking for would be...   Alacarte! ;)

Just install it if you haven't done that already, it works just fine with Unity for creating and editing your application launchers. There is no Unity-specific tool for the purpose because there si no reason to have one, Unity uses exactly the same .desktop files and menu structures every other XDG-compatible desktop environment does (and why wouldn't it, you are still running Gnome 3 desktop even with Unity session).

I'll try alacarte again but its not installed by default is there a way to install it without gnome3 fallback dependencies?

When I used alacarte in 11.04 it just edited existing icons and didn't make new ones.

---

### Post by Krytarik on 2012-01-11
> **Topazkitty said:**
> I'll try alacarte again but its not installed by default is there a way to install it without gnome3 fallback dependencies?
Yup, by running:
```
sudo apt-get install --no-install-recommends alacarte
```> **Topazkitty said:**
> When I used alacarte in 11.04 it just edited existing icons and didn't make new ones.
Well, you can also create "New Item"s with it, even in Lucid 10.04, so this wasn't just introduced anywhere near recently ([changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/a/alacarte/alacarte_0.13.2-2ubuntu3/changelog")).

Regards.

---

### Post by Topazkitty on 2012-01-11
> **Krytarik said:**
> Yup, by running:
```
sudo apt-get install --no-install-recommends alacarte
```Well, you can also create "New Item"s with it, even in Lucid 10.04, so this wasn't just introduced anywhere near recently ([changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/a/alacarte/alacarte_0.13.2-2ubuntu3/changelog")).

Regards.

Hi, thanks for suggestion and the application did not install with dependencies however, when I try to launch it and make a menu change to test it It doesn't even work even though i'm clicking the add item.

Here is the error message I got in terminal

amanda@Amanda-1525:~$ alacarte

(alacarte:2959): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(alacarte:2959): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(alacarte:2959): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(alacarte:2959): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

---

### Post by Krytarik on 2012-01-11
> **Topazkitty said:**
> ... when I try to launch it and make a menu change to test it It doesn't even work even though i'm clicking the add item.

Here is the error message I got in terminal
```
[..]
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 311, in on_new_item_button_clicked
    process = subprocess.Popen(['**gnome-desktop-item-edit**', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] **No such file or directory**
[..]
```
Turns out that "gnome-panel" should be actually marked as a "dependency" instead of just a "recommended" package:

content of package "gnome-panel":
> /usr/bin/**gnome-desktop-item-edit**
/usr/bin/gnome-panel
/usr/bin/panel-test-applets
/usr/lib/gnome-panel/4.0/libclock-applet.so
/usr/lib/gnome-panel/4.0/libfish-applet.so
/usr/lib/gnome-panel/4.0/libnotification-area-applet.so
/usr/lib/gnome-panel/4.0/libwnck-applet.so
/usr/lib/gnome-panel/gnome-panel-add
/usr/share/applications/gnome-panel.desktop
/usr/share/doc/gnome-panel/AUTHORS
/usr/share/doc/gnome-panel/NEWS.gz
/usr/share/doc/gnome-panel/README
/usr/share/doc/gnome-panel/changelog.Debian.gz
/usr/share/doc/gnome-panel/copyright
/usr/share/man/man1/gnome-desktop-item-edit.1.gz
/usr/share/man/man1/gnome-panel.1.gz
/usr/share/man/man1/panel-test-applets.1.gz[http://packages.ubuntu.com/oneiric/i386/gnome-panel/filelist](http://packages.ubuntu.com/oneiric/i386/gnome-panel/filelist)

But you can install "gnome-panel" without pulling *its* "recommends", particularly the Gnome Fallback sessions, that is:
```
sudo apt-get install --no-install-recommends gnome-panel
```Related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/656735](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/656735)

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/826049](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/826049)

---

### Post by Topazkitty on 2012-01-11
with the gnome-session added it works to edit items now but when I added a firefox link to the games menu as a test it doesn't actually show up in unity's menu like 11.04

---

### Post by mcduck on 2012-01-12
> **Topazkitty said:**
> with the gnome-session added it works to edit items now but when I added a firefox link to the games menu as a test it doesn't actually show up in unity's menu like 11.04

Unity usually needs to be restarted (ot you have to log out and back again) before it recognizes new manually made changes in menus.

---

### Post by Topazkitty on 2012-01-12
> **mcduck said:**
> Unity usually needs to be restarted (ot you have to log out and back again) before it recognizes new manually made changes in menus.

I tried that and it still doesn't work. any other ideas?

thanks

---

### Post by Krytarik on 2012-01-12
> **Topazkitty said:**
> I tried that and it still doesn't work.
Then you must be doing something wrong, I've successfully tested that earlier today. Any details reg. the intended launchers!?

Incidentally, you only need to "killall unity-applications-daemon" to make Unity reload it, and therefore the launchers, the next time you search the Dash for apps.

---

### Post by Topazkitty on 2012-01-12
> **Krytarik said:**
> Then you must be doing something wrong, I've successfully tested that earlier today. Any details reg. the intended launchers!?

Incidentally, you only need to "killall unity-applications-daemon" to make Unity reload it, and therefore the launchers, the next time you search the Dash for apps.

For testing I am trying to make a firefox launcher in my games folder called unity test. I want to actually add links to flash games in my games menu later.

I just tried the command above after editing the menu and it doesn't show my firefox link under the game section.

I've had this problem since 11.04.

the menu edit is there If i start typing in dash but I shouldn't have to search for it. I thought it would be in the correct section

thanks for trying to help me everyone

---

### Post by Krytarik on 2012-01-12
> **Topazkitty said:**
> ... it doesn't show my firefox link under the game section. ... the menu edit is there If i start typing in dash but I shouldn't have to search for it. I thought it would be in the correct section
Ok, to that effect, it's true, the launchers are _not_ sorted to the menus like set up with Alacarte!
So it's true as well that Alacarte is not sufficiently supporting Unity!

This is because Alacarte doesn't store the "Categories" in the .desktop files of the respective apps, but uses the [Desktop Menu Specification]("http://standards.freedesktop.org/menu-spec/menu-spec-latest.html") for them, which Unity apparently doesn't take into account.

In your case that means you would have to manually add the proper "Categories" keys to the .desktop files of your games; you will find them under "~/.local/share/applications" in your home directory, you need to open them from *inside* the text editor.

As these are web browser games and you want to run them with Firefox, they aren't environment-specific at all, so "Categories" like this would be appropriate:
```
Categories=Game;
```For comparison, the "Categories" of Mahjongg are:
```
Categories=GNOME;GTK;Game;BoardGame;
```Of course, you could add corresponding sub-categories to them, but that obviously wouldn't matter in Unity as you can't filter them down any more than to "Games". ;-)

---

### Post by Topazkitty on 2012-01-13
> **Krytarik said:**
> Ok, to that effect, it's true, the launchers are _not_ sorted to the menus like set up with Alacarte!
So it's true as well that Alacarte is not sufficiently supporting Unity!

This is because Alacarte doesn't store the "Categories" in the .desktop files of the respective apps, but uses the [Desktop Menu Specification]("http://standards.freedesktop.org/menu-spec/menu-spec-latest.html") for them, which Unity apparently doesn't take into account.

In your case that means you would have to manually add the proper "Categories" keys to the .desktop files of your games; you will find them under "~/.local/share/applications" in your home directory, you need to open them from *inside* the text editor.

As these are web browser games and you want to run them with Firefox, they aren't environment-specific at all, so "Categories" like this would be appropriate:
```
Categories=Game;
```For comparison, the "Categories" of Mahjongg are:
```
Categories=GNOME;GTK;Game;BoardGame;
```Of course, you could add corresponding sub-categories to them, but that obviously wouldn't matter in Unity as you can't filter them down any more than to "Games". ;-)


Thanks for all of your help but can you explain to me how to do this step by step because I don't generally mess with text files like this.

---

### Post by Krytarik on 2012-01-13
> **Topazkitty said:**
> ... can you explain to me how to do this step by step ...
Please not! [-o< :P I hope this is already step-by-step'ish enough:
> **Krytarik said:**
> In your case that means you would have to  manually add the proper "Categories" keys to the .desktop files of your  games; you will find them under "~/.local/share/applications" in your  home directory, you need to open them from *inside* the text editor.

As these are web browser games and you want to run them with Firefox,  they aren't environment-specific at all, so "Categories" like this would  be appropriate:
```
Categories=Game;
```
One noteworthy detail to add, though, is that your created .desktop files will be named like this:
```
~/.local/share/applications/alacarte-made.desktop
~/.local/share/applications/alacarte-made-1.desktop
~/.local/share/applications/alacarte-made-2.desktop
```... and so on.

This is how it looks in the text editor's Open/Save dialogs, not in   Nautilus, there their names reflect the values of their "Name" keys!

---

### Post by Topazkitty on 2012-01-13
> **Krytarik said:**
> Please not! [-o< :P I hope this is already step-by-step'ish enough:

One noteworthy detail to add, though, is that your created .desktop files will be named like this:
```
~/.local/share/applications/alacarte-made.desktop
~/.local/share/applications/alacarte-made-1.desktop
~/.local/share/applications/alacarte-made-2.desktop
```... and so on.

This is how it looks in the text editor's Open/Save dialogs, not in   Nautilus, there their names reflect the values of their "Name" keys!

I understand what your trying to tell me but i'm confused how to make the files from scratch can you post a sample of one the entries?

---

### Post by Krytarik on 2012-01-13
> **Topazkitty said:**
> I understand what your trying to tell me but i'm confused how to make the files from scratch ...
Just create them with Alacarte first, then just add the missing "Categories" line to them (the placing doesn't matter).

---

### Post by Krytarik on 2012-01-13
> **Topazkitty said:**
> ... can you post a sample of one the entries?
However, this is the full content of Mahjongg's .desktop file:

/usr/share/applications/mahjongg.desktop:
```
[Desktop Entry]
Name=Mahjongg
Comment=Disassemble a pile of tiles by removing matching pairs
Exec=/usr/games/mahjongg
Icon=gnome-mahjongg
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;BoardGame;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-games
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.30.0
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-games
```

---

### Post by Topazkitty on 2012-01-13
> **Krytarik said:**
> However, this is the full content of Mahjongg's .desktop file:

/usr/share/applications/mahjongg.desktop:
```
[Desktop Entry]
Name=Mahjongg
Comment=Disassemble a pile of tiles by removing matching pairs
Exec=/usr/games/mahjongg
Icon=gnome-mahjongg
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;BoardGame;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-games
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.30.0
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-games
```

That workaround does work now. Should I file a bug report so this can fixed either in this release or 12.04?

---

### Post by Krytarik on 2012-01-13
> **Topazkitty said:**
> Should I file a bug report so this can fixed either in this release or 12.04?
Checking Launchpad for already existing bug reports reg. that, I learned that you've already filed one against Alacarte:

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/797332](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/797332)

Like me, they too aren't considering it as a bug, but as a missing feature (their corresponding status for the importance is "Wishlist"), because Alacarte is utilizing a valid specification for menu systems.

The same is true for Unity, because it's not exactly a "menu" system, so it may not be obligated to respect a menu specification:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762291](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762291)

So in your case I would just leave a new comment on your existing bug report, to make the devs aware of it again.

---

### Post by Topazkitty on 2012-01-13
Thank you so much for all of your help hopefully they add this feature to Ubuntu eventually.

---

