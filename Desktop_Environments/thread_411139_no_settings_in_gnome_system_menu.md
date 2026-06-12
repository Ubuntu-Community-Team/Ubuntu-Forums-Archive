---
title: "no settings in gnome system menu"
date: 2007-04-16
forum: Desktop Environments
---

### Post by roketa on 2007-04-16
I formated my home partition. After I recovered it I have lost some files. Among other things I don't have settings and administration entries in system menu, only help and about items. Is there any way I can restore system menu?

---

### Post by hackerssidekick on 2007-04-17
Run alacarte, and see if it's somehow been disabled in there.

---

### Post by roketa on 2007-04-17
if I try to run alacarte I get this:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 56, in __loadMenus
    self.settings.dom = xml.dom.minidom.parse(self.settings.path)        
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 0

---

### Post by hackerssidekick on 2007-04-17
hmmm looks like the menu is corrupt or something (it fails trying to parse the menu file).

Attach these files to your reply: /etc/xdg/menus/applications.menu, /etc/xdg/menus/preferences.menu and /etc/xdg/menus/settings.menu

Edit: did some searching, and one thing you can try is a program called update-menus. Install a package called **menu-xdg** and it's dependancy **menu**, and then run this command:
```
update-menus -v -d
```

It will print out some messages and exit, something like "running method...", and your menus should be back (hopefully).

---

### Post by roketa on 2007-04-18
**from preferences.menu:**

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
  <Name>Preferences</Name>
  <Directory>Preferences.directory</Directory>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Ensure we read from the old capplets .desktop location -->
  <LegacyDir>/usr/share/control-center-2.0/capplets</LegacyDir>

  <!-- Read in overrides and child menus from preferences-merged/ -->
  <DefaultMergeDirs/>

  <!-- Stuff in the toplevel -->
  <Include>
    <And>
      <Category>Settings</Category>
      <Not>
        <Or>
          <Category>System</Category>
          <Category>Accessibility</Category>
        </Or>
      </Not>
    </And>
  </Include>

  <!-- Menu items to exclude from the toplevel -->
  <Exclude>
    <Filename>gnomecc.desktop</Filename>
  </Exclude>

  <!-- Accessibility -->
  <Menu>
    <Name>Accessibility</Name>
    <Directory>Settings-Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>Accessibility</Category>
      </And>
    </Include>
  </Menu>

</Menu>     <!-- End Prefs -->

**from settings.menu:**

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Desktop</Name>
  <Directory>Desktop.directory</Directory>

  <!-- Ensure we read from the old capplets .desktop location -->
  <LegacyDir>/usr/share/control-center-2.0/capplets</LegacyDir>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Read in overrides and child menus from applications-merged/ -->
  <DefaultMergeDirs/>

  <!-- Add a link to the control center -->
  <Include>
    <Filename>gnomecc.desktop</Filename>
  </Include>

  <!-- Merge in these other files as submenus -->
  <Menu>
    <Name>Preferences</Name>
    <MergeFile>preferences.menu</MergeFile>
  </Menu>

  <!-- System Settings -->
  <Menu>
    <Name>Administration</Name>
    <Directory>System-Settings.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>System</Category>
      </And>
    </Include>
  </Menu>     <!-- End System Settings -->

  <Layout>
    <Menuname>Preferences</Menuname>
    <Menuname>Administration</Menuname>
  </Layout>

</Menu> <!-- End Settings -->



**update-menus -v -d returned:** 

update-menus[9907]: Update-menus is run by user.
update-menus[9907]: Dpkg is not locking dpkg status area, good.
update-menus[9907]: Reading installed packages list...
update-menus[9907]: Reading menu-entry files in /home/rok/.menu/.
update-menus[9907]: 0 menu entries found (0 total).
update-menus[9907]: Reading menu-entry files in /etc/menu/.
update-menus[9907]: 0 menu entries found (0 total).
update-menus[9907]: Reading menu-entry files in /usr/lib/menu/.
update-menus[9907]: 2 menu entries found (2 total).
update-menus[9907]: Reading menu-entry files in /usr/share/menu/.
update-menus[9907]: 130 menu entries found (132 total).
update-menus[9907]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[9907]: file /usr/share/menu/default/ash line 2:
Discarding entry requiring missing package ash.
update-menus[9907]: 0 menu entries found (132 total).
update-menus[9907]: Running menu-methods in /home/rok/.menu-methods/.
update-menus[9907]: Running menu-methods in /etc/menu-methods/.
update-menus[9907]: Running method: /etc/menu-methods/gnome-panel-data
update-menus[9907]: Running method: /etc/menu-methods/xdg-desktop-entry-spec-dirs
update-menus[9907]: Running method: /etc/menu-methods/xdg-desktop-entry-spec-sessions
update-menus[9907]: Running method: /etc/menu-methods/menu-xdg
update-menus[9907]: Running method: /etc/menu-methods/xdg-desktop-entry-spec-apps

still no menus...

---

### Post by saxonjf on 2007-04-18
How does one run alacarte?  I can't find it anywhere

How does one install a package, such as menu-xdg?

---

### Post by roketa on 2007-04-20
Well, I found control center in "add to panel" options.  More or less this saves my problem. I still can't edit main menu  though.

---

### Post by hackerssidekick on 2007-04-20
> **saxonjf said:**
> How does one run alacarte?  I can't find it anywhere

How does one install a package, such as menu-xdg?

Two ways:
[LIST=1]
[*]By using the "Add/Remove" menu item in the Applications menu. Just search for the package name and the rest is simple :)
[*]In a terminal (Applications->Accessories->Terminal), first update the list of packages by typing in **sudo apt-get update**, and then install packages by **sudo apt-get install <package-name>**. If you don't know the exact name of a package, you can search by **apt-cache search <string>**
[/LIST]

Alacarte can be run in the terminal, or you can run it via gnome's Run Application dialog (bring it up by pressing <Alt>-<F2>.

---

### Post by roketa on 2007-05-07
I finaly solved my problem. I followed this recommendation "If one removes or moves ~/.config and ~/.local/share the original menus are restored". I had some write protected files in there which rm command warned me of. I didn't delete those.

---

