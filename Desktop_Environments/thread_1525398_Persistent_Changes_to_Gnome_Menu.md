---
title: "Persistent Changes to Gnome Menu"
date: 2010-07-06
forum: Desktop Environments
---

### Post by lojack2374 on 2010-07-06
[I]Hello all.

I'm trying to figure out how to make persistent changes to the Gnome
menu. I know I can make user-specific changes, as defined by Alacarte,
but that's not what I need for this machine. I'm running Ubuntu 10.04
with Gnome 2.30.2.

Per freedesktop.org specs I created an entry for a new sub-menu under
Applications called Social Networking. I simply copied an existing menu
entry and made the appropriate changes. For example:
  <!-- Social Networking -->
  <Menu>
    <Name>Social</Name>
    <Directory>Social-Networking.directory</Directory>
    <Include>
      <And>
        <Category>Social</Category>
      </And>
    </Include>
  </Menu>

Next I created a .desktop file in /usr/share/desktop-directories/ called
Social-Networking.directory.
  [Desktop Entry]
  Name=Social
  Comment=Social Networking Applications and Utilities
  Icon=preferences-system-network
  Type=Directory
  X-Ubuntu-Gettext-Domain=gnome-menus

Now, I'm stuck. I can't seem to figure out how to make an application's
menu appear in the Social Networking sub-menu. For that matter, I can't
even get the Social Networking sub-menu to appear under Applications. I
assuming it will appear once I "associate" an applications's menu to the
sub-menu, but I'm only guessing right now. I've logged out and back in;
I even restarted my machine. Though I am not new to Linux, I am new to
Ubuntu and Gnome.

Any hints or suggestions would be greatly appreciated. In the meantime,
I'll continue reading freedesktop.org specs.

TIA


--
Chris
[/I]

---

### Post by Brandon Williams on 2010-07-07
> **lojack2374 said:**
> I assume it will appear once I "associate" an applications's menu to the sub-menu, but I'm only guessing right now.

I believe that you are correct about this. XFCE does not display empty menus, and I believe this is true of Gnome, too. If you have configured everything about the new menu correctly (it seems that you have), then adding an application to the menu should make the menu appear. Create a .desktop file for the application in /usr/share/applications/ with "Categories=Social;" and see if that is enough to make the menu show up. You might have to log out and log back in, but I don't think so.

---

