---
title: "Cannot Change Opera Icon"
date: 2010-05-06
forum: Desktop Environments
---

### Post by VJgamer on 2010-05-06
I am running kubuntu 10.04 (32 bit) and have installed the latest version of the Opera 10.53 beta.

My problem is that I cannot change the icon for Opera in the Kickoff menu or on the desktop. I tried right clicking on the Kickoff Application Launcher widget on the panel and choosing Menu Editor; Navigated to Opera and changed the icon from the default KDE icon (opera) to the new styled Opera icon (opera-browser), but it doesn't change. Any suggestions?

---

### Post by Zorael on 2010-05-08
It seems the task manager takes hints directly from the application as to what icon it should use. The menu and the launch notification icon by the mouse cursor listens to the applications .desktop file (in **/usr/share/applications**) or user-specific overrides (in **~/.local/share/applications**).

KDE apps can be started with an argument overriding that, like '**konsole --icon acroread**' to make Konsole use the acroread icon. (acroread name taken from the icon browser)

Perhaps Opera has a similar command-line argument? If so you could just modify the launcher you use to pass it upon program start.

---

### Post by VJgamer on 2010-05-08
When Opera is running the task manager and the opera window have the correct icon. It is only in the task launcher and the desktop icon. If I navigate to ~/.local/share/applications and try to change the opera-browser.desktop file, no matter which opera icon I use it still uses the default KDE one.

I'm fairly certain it's a KDE icon because Gnome just uses the icon that comes with Opera, but I really like KDE.

If I try creating a new shortcut and chose the default Opera icon it gets changed to the KDE icon. If I open up the .desktop file in an editor and change the icon name manually it still doesn't change. It will let me however change it to another applications icon, just not any of the other Opera icons.

---

### Post by Zorael on 2010-05-08
> **VJgamer said:**
> the icon for Opera in the Kickoff menu or on the desktop.
I see; I misread this.

I can't find the *opera-browser* icon you mention, but I am able to change the icon. This via the menu editor, and by right-clicking a Folder View widget, then Create New -> Link To Application, pointing it to **/usr/bin/opera** and picking the icon I want.

There is a standard Oxygen icon¹ for Opera that's bundled in the **kdebase-data** package. I imagine this is the default KDE icon you mention. The Opera package itself (from the site) seems to come with its own hicolor icon². Is that the "new styled Opera icon" you want to change to? See attached screenshots.


¹: **/usr/share/icons/oxygen/48x48/apps/opera.png**
²: **/usr/share/icons/hicolor/128x128/apps/opera.png**

---

### Post by VJgamer on 2010-05-08
The icon in your screen shots is exactly the icon I am trying to get. I finally have that icon now. What I had to do was rename the following icons to opera.pn_:

/usr/share/icons/oxygen/48x48/opera.png
/usr/share/icons/oxygen/32x32/opera.png
/usr/share/icons/oxygen/16x16/opera.png

Now that they are gone it automatically uses the HiColor icon that comes with Opera. I am unsure why simply changing the icon in the Menu Editor would not work. I was going to take a video of what was happening; perhaps I should file a bug report?

Thank you very much Zorael.

---

### Post by Zorael on 2010-05-08
Cheers.

As for a bug report; if you can readily reproduce it, perhaps. I merely went into the menu editor, found Opera under Internet, hit the icon, chose Other, and then maneuvered to that hicolor opera.png file. The resulting **~/.local/share/applications/opera.desktop** file looked like the following excerpt;
```
[Desktop Entry]
Categories=Application;Qt;Network;WebBrowser;X-Ximian-Main;X-Ximian-Toplevel
Comment=Web Browser
Encoding=UTF-8
Exec=opera %u
GenericName=Web browser
**Icon=/usr/share/icons/hicolor/128x128/apps/opera.png**
*[...]*
```
If it really really won't do that for you, you could also try to clear the icon cache by running '**kbuildsycoca4 --noincremental**' in a terminal.

And if it really doesn't work even after that, then yes, you could try filing a bug report.

---

### Post by VJgamer on 2010-05-08
OK, I see where we get different results. When I go to change the icon, the hicolor icon shows in the 'System icons' list along with the oxygen icon. However, when you choose the hiclor icon from there it keeps the oxygen icon.

When I choose 'Other icons' and browse to /usr/share/icons/hicolor/128x128/apps/opera.png it does in fact change the icon.

My opera.desktop file had this for icon:
```
Icon=opera-browser
```

Which I thought would work given the options on my screen for which I've included a screenshot.

---

