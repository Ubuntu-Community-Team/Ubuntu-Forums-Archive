---
title: "No tabs in Terminal? Configuring Desktops? Confingring Launcher"
date: 2012-01-29
forum: Desktop Environments
---

### Post by rpaskudniak on 2012-01-29
Greetings after a loooong hiatus.

I finally got off my fence and on by backside, installing the 10-11 version of Ubuntu.  I am still using the Gnome desktop, though I didn't specify "Classic Gnome" at login.  This is the first time I have looed in since the upgrade a fwe hours ago.

I am not pleased with what I see just yet but I hope someone can point me to the appropriate new actions.  I tried to search on "Terminal Tabs" before posting this.

[LIST=1]
[*]The previous Gnome desktop had a tool for me to configure the launcher  menus and submenus. I had a menu on top ([Application] [Places] [System]) and I was able to configure the menus from a tab in "User Settings".  I now see no such tab and right-clicking on the launch bar provides nothing useful.  And the icons in the launch bar are big so they need to squeeze & scroll.
[*]Previously, the Terminal window had a menu bar that, among other useful stuff, allowed me to open multiple sessions, each in its own tab and with its own properties, in the same window.  I don't see that here. I want it back!
[*]In my previous gnome I was able to right-click on the "desktops" icon in the bottom bar and decide I want 6 desktops. No such capability here?
[/LIST]
<Sigh...>

Anyone up to to the task of making a minor Ubuntu veteran not get turned back into a newbie? :confused:

---

### Post by mcduck on 2012-01-29
1. All the application launchers can still be configured using exactly the same tool as before. You'll find it if you search for "Main Menu" in the Dash. (if you for some reason don't have it, install "alacarte" package. Although I'm pretty sure it's installed by default).

The launcher panel can be configured using [CompizConfig Settings Manager]("apt:compizconfig-settings-manager"), (under Ubuntu Unity Plugin, Experimental-tab) or [Ubuntu Tweak]("apt:ubuntu-tweak") (Tweaks->Unity Settings). You'll find the option for icon size in both of these tools.

2. The menu bar for the terminal, just like for all the other programs, appears in the top panel when you move the mouse cursor over the programs name in the top left corner.

3. CompizConfig Settings Manager is your friend, once again. You can configure the amount of desktops under General settings, on the "Desktop Size"-tab.

Be careful with CCSM, though, some of the plugins and options will conflict with the default Unity settings, so pay close attention to any possible warning messages about conflicting options or you might end with a on-functional Unity desktop. In that case running "unity --reset" in a terminal should fix the settings so that Unity works again.)

edit: So are you actually using Gnome Shell, Unity, or Classic Gnome? If you aren't using Unity then of course ignore everything about CCSM or Ubuntu-Tweak. Main Menu-tool works fine for Shell as well, terminal's menu should be visible by default but if not, right-click in the terminal and select "Show Menubar". And the amount of desktops in Gnome Shell is flexible, it will always automatically add you new empty desktops when you open applications in the existing ones, making sure you always have one free desktop available. And whichever you sue, Shell or Unity, the icon size in the menu itself isn't configurable, at least not in current versions...

---

### Post by rpaskudniak on 2012-02-05
Sighh.. McDuck, Thank you for your patient explanation. I had to wait until I logged back in to Ubunto to the "Ubuntu" desktop (as opposed to Gnome classic) before trying out your suggestions.  Though they read as straightforward tips, they do not execute so simply.
> 1. All the application launchers can still be configured using exactly the same tool as before. You'll find it if you search for "Main Menu" in the Dash.
Well, I have the Alacarte app installed but no Main Menu in the Dash.  (I presume that by the "Dash" you refer the column of icons to the left of the screen)  I did click the "Dash Home" icon on top and typed "Main" into the search bar, which allowed me to open Main Menu. When an icon for said Main Menu appeared in the Dash I right-clicked on it and selected "Keep in launch".  Sot it's there now.  Er.. What I get is the ability to edit the Main Menu.  Thus far, I have found no way to actually display the main menu, to select an item therefrom and run it.  I'm all ears on how I can get that.
> The launcher panel can be configured using CompizConfig Settings Manager, (under Ubuntu Unity Plugin, Experimental-tab) or Ubuntu Tweak (Tweaks->Unity Settings). You'll find the option for icon size in both of these tools.
CompizConfig Settings: That's a new one on me. (So I'm ignorant of some details :( ) That I could not find in the Dash search bar as I did above.  But I opened a Terminal and typed compiz:
```
$ compiz
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
```
That ain't goin' nowhere nohow!
So how do you propose I execute compiz?  Synaptic shows me it is installed, I merely seem to have no path toward running it in my current state.
> 2. The menu bar for the terminal, just like for all the other programs, appears in the top panel when you move the mouse cursor over the programs name in the top left corner.
Interesting new behavior.  Thank you for pointing it out.

I suppose the argument may be made for moving the menu bar of the currently active window up to the top panel but after so many years of finding it in below the title bar of every blessed application I run, it is quite counter-intuitive to suddenly hide it from the user.  It also forces more mouse movement to accomplish everything.  I would configure it back to my application windows, should I ever figure out how to do this configuration. (I probably will, eventually.)  FWIW, I do NOT like this feature.  Who asked for it?
> 3. CompizConfig Settings Manager is your friend, once again. You can configure the amount of desktops under General settings, on the "Desktop Size"-tab.
Oh, that elusive friend.  Would someone please introduce me and explain how to get this compiz running?

If I can get past these hurdles, I might become a great fan of the new look.  But right now, the path of least resistance for me is to go back to the familiar Gnome-Classic desktop.  Though I'd like to get the [System] menu back up top with the [Applications] and [Places] menus.

As I said above, I'm all ears.

([I][SIZE="1"]Whoops! I just realized I misspelled "Configuring" in the thread subject line.  I'll see if I can fix this with an edit.[/SIZE]/I])

---

### Post by mcduck on 2012-02-05
If you are using Unity desktop, then Compiz is already running. So no need to worry about that. And [CompizConfig Settings Manager]("apt:compizconfig-settings-manager") isn't installed by default, so you need to install it yourself. Just get it from the Software Center if you want (Although [Ubuntu-Tweak]("apt:ubuntu-tweak") might be a bit easier option, CCSM has *lots* of settings and can be a bit confusing.)

...and Dash is the window that opens when you click the Ubuntu button, while the panel on the left-hand side of the desktop (with all the icons) is simply called "Launcher Panel" (an icon used to start an application being called "Launcher" on most Linux desktop environments).

What comes to Main Menu, it applies to pretty much every menu system used on various desktop environments, including Unity's Dash. So if you create a program launcher with it, the program will then appear in the Dash, both in the searches and when browsing through the Applications lens of the Dash. (You might have to log out and back after creating a new launcher before Unity sees it). After that you can just drag&drop the launcher from Dash to the Launcher Panel or to desktop.

(if you make lots of desktop launchers all the time, there is a simple trick using the Templates feature of the file manager to create them from the right-click menu. Just tell me if you want me to give instructions for that, although I can't really see why somebody would ever need to make new launchers that often. Not that I'd really see the point of even having desktop icons when both the Launcher Panel and Dash (especially the search) are so much more accessible ways to start applications. But of course we al have our own, sometimes strange, preferences... :))

---

