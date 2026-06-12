---
title: "I removed the LXDE &quot;Preferences&quot; submenu from the main menu!"
date: 2010-12-17
forum: Desktop Environments
---

### Post by spamhog on 2010-12-17
:o  How do I open the menu  prefs from "Run" ?

I was changing the visibility of main menu items, and noticed two instances of "Preferences" - one at the main level and one nested inside (if I recall correctly) "System Tools" - which didn't actually show on the menu.

I must have hidden the wrong one, or messed with a target instead of a "link"! 

Now all of "Preferences" is gone! Catch-22: I can't fix the main menu because the main menu preferences are inside the submenu I just hid!

**How do I call up the LXDE "Main Menu" preferences from command line?**

or

[B]Can I copy back the "Preferences" section from another, not-messed-up account?
In this case, from which file?[/B]

Thank you in eager anticipation!

---

### Post by SteveDee on 2010-12-17
The overall structure of the menu is controlled by: /etc/xdg/menus/lxde-applications.menu

This is an XML file with sections like this (the Preferences item is actually called settings):-
```

	<Menu>
		<Name>DesktopSettings</Name>
		<Directory>lxde-settings.directory</Directory>
		<OnlyUnallocated/>
		<Include>
			<Or>
				<Category>Settings</Category>
				<Category>PackageManager</Category>
				<Category>System</Category>
			</Or>
		</Include>
		<Layout>
			<Merge type="menus"/>
			<Merge type="files"/>
		</Layout>

	</Menu> <!-- End Settings -->

```
This references the lxde-{name}.directory files in: /usr/share/desktop-directories
(e.g. lxde-settings.directory)

The settings.directory file looks like this:-
[Desktop Entry]
Name=Preferences
Comment=Personal preferences
Icon=preferences-desktop
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus

---

### Post by spamhog on 2010-12-18
Thank you SteveDee!

I indeed found that this line was missing from my
/usr/share/desktop-directories/lxde-settings.directory file:

X-Ubuntu-Gettext-Domain=gnome-menus

This is a system-wide setting. How could it have changed through the Main Menu dialog, which is user level?

---

### Post by spamhog on 2010-12-18
OK, solved.

- logged in as another user

- looked into the properties of the entry 
LXDE Menu / Applications / Preferences / Main Menu

- the command was "alacarte" and it did NOT require sudo

- hence, at least not not DIRECTLY a systemwide issue, as in
/etc/xdg/menus/lxde-applications.menu
or
/usr/share/desktop-directories/lxde-settings.directory

- logged back in as myself

- ran alacarte

- made the submenu
LXDE Menu / Preferences
visible again

- but discovered another can of worms (see new thread [http://ubuntuforums.org/showthread.php?t=1648090&highlight=lxde]("http://ubuntuforums.org/showthread.php?t=1648090&highlight=lxde"))

---

