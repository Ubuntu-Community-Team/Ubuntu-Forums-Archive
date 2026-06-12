---
title: "Maori Keyboard Layout"
date: 2006-04-04
forum: Desktop Environments
---

### Post by HoustonHeightsGuy on 2006-04-04
Has anyone EVER figured out how to make the dead key ( ` ~ ) on the Maori keyboard layout work?

I type a lot of text and it's very burdensome to keep going to special characters in Open Office to retrieve the macroned vowels.

Shortcuts and so forth are not the answer, as five different vowel characters are required - only a dead key will do, such as are used on several other language kb layouts (like Greek, for instance). 

As a rather green beginner in Linux, I probably need step-by-step help.

Thanks in advance for any help !!!

---

### Post by gingermark on 2006-04-04
If you install and run the package KKBSwitch you should then be able to then add a new keyboard layout (Greek if you like) and easily switch between it and your current layout. Maybe not ideal, but that could be a way to get the effect you want.
[LIST=1]
[*]K-Menu --> System --> Konsole. This will open up a terminal emulator.
[*]Type 'kdesu kate /etc/apt/sources.list' then enter your user password when prompted. This will open up a text editor with root priviledges allowing you to edit the file that lists the repositories that you can access to install programs.
[*]Remove any '#' symbols from the beginning of any lines. This will enable these repositories. Specifically, the package we're looking for is in the universe repository, so make sure that one in partuclar is not preceded with a '#'.
[*]Save the file and close the text editor
[*]In Konsole type 'sudo apt-get update'. Enter your password if prompted. This reloads your newly saved repository list so the new repositories can be used.
[*]Still in Konsole, now type 'sudo apt-get install kkbswitch'. This will install the program.
[*]Close Konsole, and go K-Menu --> System Settings --> Regional & Accessibility --> Keyboard Layout. Here you can add an additional keyboard setting (such as Greek).
[*]K-Menu --> Utilities --> KKBSwitch will start KKBSwitch. Once started you should see an icon in your taskbar. Right-click on it and select "Configure Keyboard Switch". Here you can set up an easy way to switch between your current keyboard layout and the new one (Greek).
[/LIST]

Phew! **Hopefully** that should give you an easy and quick way to access an alternate keyboard layout, and as such have access to the alternate characters you need. Thinking about it now, there might be a better way to do it, but I just typed all that, and I'm sticking with it! :)

---

