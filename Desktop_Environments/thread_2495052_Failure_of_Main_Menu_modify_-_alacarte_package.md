---
title: "Failure of Main Menu modify - alacarte package"
date: 2024-02-06
forum: Desktop Environments
---

### Post by John_Rose on 2024-02-06
Hello,

Sorry if some of the technical terms below are approximate since I am using the French interface and don't always know the equivalent in the English interface.

I am running Ubuntu 22.04 LTS with gnome 42.9 on an ASUS Vivobook 14 notebook. Even though the application menu is no longer available in the standard gnome interface (really crazy - very inefficient to use the interface options of the Activities search [you have to know something about the name of the activity to find it] or the full list of available activities [nearly useless if you have dozens of them], but the Main Menu "activity" is still available to make changes to the Main Menu.

So I rely on the Main Menu and make it available though classicmenu-indicator ([https://installati.one/install-classicmenu-indicator-ubuntu-22-04/](https://installati.one/install-classicmenu-indicator-ubuntu-22-04/)). Using this application I can call  from the Main Menu without problem the preinstalled applications and those added automatically to the Main Menu when installed through SNAP or Synaptic Package Manager.

My difficulty comes when I try to manually add a manually installed application (such as the Canon scangear package - scangearmp2) to the Main Menu, or to change the properties of an application already in the Main Menu (like adding or modifying the launch icon). When I ask to add or modify a menu element and fill out the fields and click OK, I get a system message that Main Menu has stopped unexpectedly, and my changes are not recorded in Main Menu. The package which calls Main Menu for modification is called alacarte. Synaptic tells me that the lastest version 3.44.1-1ubuntu0.1 is installed.

Could someone please help me to make the alacarte functionality to add or modify Main Menu elements work?

Thanks and best wishes,
    John

---

### Post by John_Rose on 2024-02-08
I checked the crash report for alacarte which had the line "Title: alacarte crashed with AttributeEditor in get_icon_string():'LaunchEditor' object has no attribute 'icon_file'". I saw in another posting that alacarte expects icons with a png or jpg extension. I browsed /usr/share/pixmaps/ for a jpg icon to be associated with my new Canon Scangear element, and it completed the menu addition without error. The new application in the Main Menu (alacarte) also loads without error. Perhaps the default icon proposed by alacarte (a stylized keyboard key) either has a bad link or a link to an icon in the wrong format?

---

