---
title: "Shortcut keys in Lubuntu"
date: 2013-04-28
forum: Desktop Environments
---

### Post by Svante65 on 2013-04-28
How do you make shortcut keys in Lubuntu?
To make an example I want to make Ctrl+Alt+F open Firefox and Ctrl+Alt+C to open Chromium.

---

### Post by vasa1 on 2013-04-28
You need to edit /.config/openbox/lubuntu-rc.xml. First make a backup. Then edit this file with a text editor to make whatever changes you wish.
To do what you want, after opening lubuntu-rc.xml with a text editor, look for </keyboard> on a line just by itself. Then just above that line, paste the following:
```

    <!-- Launch Chromium -->
    <keybind key="C-A-c">
      <action name="Execute">
        <command>chromium-browser</command>
      </action>
    </keybind>

```

Save the file. Then, open a terminal and type in:
```
openbox --reconfigure
```Note there are two dashes before "reconfigure", not one long one!
If you did everything correctly, there should be no error message and you'll get back your prompt.
From now on, whenever you press control+alt+C together, Chromium will open.
The most important thing is to make sure you're using a shortcut that isn't used by something else!


Read a little more here: [https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse) and the section just above it.

---

