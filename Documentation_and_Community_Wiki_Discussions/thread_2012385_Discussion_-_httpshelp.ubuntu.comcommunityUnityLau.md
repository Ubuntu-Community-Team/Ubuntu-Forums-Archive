---
title: "Discussion - https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding 

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

Support threads should be posted in normal forums.

Thank you.

---

### Post by matteosistisette on 2013-06-16
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)


The part regarding editing an entry in the launcher is either incomplete or wrong.

Specifically:

> So as to find the exact filename of the .desktop file you are interested in, open a terminal using Ctrl+Alt+T and give the following command:

```
gsettings get com.canonical.Unity.Launcher favorites
```

This will output a list of all the .desktop files you already have in your launcher, from top to bottom, like this:
```
['nautilus-home.desktop', 'firefox.desktop', 'filezilla.desktop', 'ubuntu-software-center.desktop', 'qtcreator.desktop', 'ubuntuone-installer.desktop', 'wallch.desktop', 'gnome-terminal.desktop', 'gedit.desktop', 'audacious.desktop', 'gnome-control-center.desktop']
```
(...)
Now you have in your clipboard the filename of your file, but not its path. Your file can be **either under ~/.local/share/applications/ or under /usr/share/applications/**


**OR SOMEWHERE ELSE**.

In my case the first command gives me:

```
['application://nautilus-home.desktop', 'application://gnome-terminal.desktop', '**application://google-chrome.desktop**', 'application://thunderbird.desktop', 'application://filezilla.desktop', 'application://gedit.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']

```
and I have no google.chrome.desktop file neither under ~/.local/share/applications/ or under /usr/share/applications/

If I knew the complete list of the path where to look, I would edit the wiki, but I have no idea.

---

### Post by mbuell on 2014-01-11
> **matteosistisette said:**
> [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)


The part regarding editing an entry in the launcher is either incomplete or wrong.

Specifically:



**OR SOMEWHERE ELSE**.

In my case the first command gives me:

```
['application://nautilus-home.desktop', 'application://gnome-terminal.desktop', '**application://google-chrome.desktop**', 'application://thunderbird.desktop', 'application://filezilla.desktop', 'application://gedit.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']

```
and I have no google.chrome.desktop file neither under ~/.local/share/applications/ or under /usr/share/applications/

If I knew the complete list of the path where to look, I would edit the wiki, but I have no idea.

Plus one for writing out the normal .desktop locations. I also noted the lack of that data. [COLOR=#b22222]Supposedly one (myself included) could edit that wiki - but that means I'd have to figure out how to login and all that jazz. Too many distractions atm. Those locations SHOULD be included in that wiki - very important. [/COLOR][EDIT] Strike that comment (highlighted). Strange - but for some reason my browser loaded an older version of the page (?????) - and in trying not to be lazy I tried to figure out how to edit the wiki - and it loaded an edited page which included the locations. Very odd that I should see two version without going into the wiki history tho. hmmmmm . . . 

As for if you file isn't in those locations? Sounds like time for "find" - but you probably already know that by now --- :D

---

### Post by freebird54 on 2014-01-20
I don't know if this is where this comment belongs - but rather than working to create the .desktop file for yourself - why not let Unity do it for you?  If all you want is to run the program from the Launcher....

For instance I got Sigil (ebook editor/creator) in a form that ran only from the terminal and...

1. Open terminal (using any of several methods - I dragged it from the dash to the panel)
2. Start the program running (in my case, just enter **sigil** )
3. Right click on the icon that shows up in the panel, select "Lock to launcher"

All done - no knowledge required!

```

[Desktop Entry]
Type=Application
Name=Sigil
Comment=ePUB file editor
Exec=sigil %F
Icon=sigil
Categories=Office;FileTools;Qt;Viewer;TextTools;TextEditor;Utility;
MimeType=application/epub+zip;

```


Surely this works for other things too?  :)

---

### Post by Pluvoire on 2016-04-08
1) It's probably worth adding a link to the .desktop spec ([https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)) in the "Using a Text Editor" section.

2) In the "Using a Text Editor" section:

> [COLOR=#333333][FONT=Ubuntu]One last thing to add is that by setting executable rights to your .desktop file, it automatically takes the specified Icon and Name (specified in the corresponding fields), as it should be. Be careful though, the filename doesn't really change, it still remains 'launcher_name_here.desktop' and not 'Name_field_here', the system chooses to display it like 'Name_field_here' because it's nicer without the .desktop extension.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]

Worth clarifying here that this only applies to the appearance of the launcher in *Nautilus*. If you drag a .desktop file to the Unity Launcher, it'll take on the right icon and name regardless of whether the file is set as executable.

3) In the "Adding a desktop file to the launcher" section

[/FONT][/COLOR]> [COLOR=#333333][FONT=Ubuntu]In order to add your launcher to the Unity Launcher on the left, you select and drag it onto the Launcher panel. Alternatively, you can place your .desktop file at /usr/share/applications/ or at ~/.local/share/applications/. [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]After moving your file there, search for it in the Dash (Windows key -> type the name of the application) and drag and drop it to the Unity Launcher. Now your launcher (.desktop file) is locked on the Unity Launcher! If your desktop file cannot be found by doing a search from the Dash, you may need to read on...[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]

It's not clear why anything after the first sentence is necessary. If the goal is just to get the thing on the Launcher, the first option is definitely faster and more straightforward. I guess there are side-benefits to installing to one of the applications directories - the docs should probably mention what those are.

Also, the third paragraph in this section is confusing because it makes it sound like a necessary step (it's not), and it's not really in the right order. It's essentially another way of moving the file to /usr/share/applications/, after which you can search for it and drag it to the launcher. That's not really clear from the wording.

(Sorry, I wish I could just go ahead and make the edits for this myself, but the page is marked as "Immutable". I don't know if that just means I need to wait to be added to the right permissions group, or if this is like a "locked" page on Wikipedia.)[/FONT][/COLOR]

---

