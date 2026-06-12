---
title: "Edit Gnome menus in text editor?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by DavidBiesack on 2011-03-29
I've found the Gnome UI for editing menus a bit tedious; for example, there is no way to copy a menu entry! I want to add several similar entries, for doing ssh -X to various systems.

This page[1] describes the menu files/locations but when I added a "Remote Systems" menu to my Application menu, I see no evidence of it in my ~/.config/menus/application.menu (nor in /etc/xdg/menus/applications.menu but I would not expect a user customization to show up there)

I'm fine with editing XML in Emacs if I just knew where to look. This superuser thread [2] is close but the locations it mentioned don't exist in my sustem or describe editing global menus, not ~/.config per-user menus. Where should I look?

1: [http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en")
2: [http://superuser.com/questions/68089/how-can-i-add-menu-items-to-the-gnome-applications-menu-from-the-command-line]("http://superuser.com/questions/68089/how-can-i-add-menu-items-to-the-gnome-applications-menu-from-the-command-line")

---

### Post by Krytarik on 2011-03-29
Ok, I did some practical research, meaning adding some submenus and submenu items and see what effect that has on "applications.menu".

It turned out that when you add a custom submenu and custom item via the GUI, it ends up like this in "applications.menu":
```
    <Menu>
        <Name>alacarte-made</Name> **[COLOR=Red](1)[/COLOR]**
        <Directory>alacarte-made.directory</Directory> **[COLOR=Red](2)[/COLOR]**
        <Include>
            <Filename>alacarte-made.desktop</Filename> **[COLOR=Red](3)[/COLOR]**
        </Include>
    </Menu>

```(1) gets pulled from (2)
(2) points to the file "~/.local/share/desktop-directories/alacarte-made.directory"
(3) points to the file "~/.local/share/applications/alacarte-made.desktop"

And when you change the position of the submenu, it gets listed into the layout section:
```
    <Layout>
        <Merge type="menus"/>
        <Menuname>Accessories</Menuname>
[COLOR=Blue][B]        <Menuname>alacarte-made</Menuname>
[/B][/COLOR]        <Menuname>Debian</Menuname>
        <Menuname>Education</Menuname>
        <Menuname>Games</Menuname>
        <Menuname>Graphics</Menuname>
        <Menuname>Internet</Menuname>
        <Menuname>Office</Menuname>
        <Menuname>Other</Menuname>
        <Menuname>Development</Menuname>
        <Menuname>Science</Menuname>
        <Menuname>Multimedia</Menuname>
        <Menuname>System</Menuname>
        <Menuname>Universal Access</Menuname>
        <Menuname>wine-wine</Menuname>
        <Separator/>
        <Filename>Run Application....desktop</Filename>
        <Filename>ubuntu-software-center.desktop</Filename>
        <Merge type="files"/>
    </Layout>

```
Greetings.

---

### Post by DavidBiesack on 2011-03-30
> **Krytarik said:**
> Ok, I did some practical research, meaning adding some submenus and submenu items and see what effect that has on "applications.menu".
[...]
1) gets pulled from (2)
(2) points to the file "~/.local/share/desktop-directories/alacarte-made.directory"
(3) points to the file "~/.local/share/applications/alacarte-made.desktop"
[...]
Greetings.

Thank you so much! I had tried a find(1) for 'alacart*' in ~/.config but did not know about ~/.local

I'll see if I can figure out who can update the Gnome doc at [http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en](http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en) which does not mention ~/.local

UPDATE: I found the ~/.local files documented a bit at [Desktop Menu Specification]("http://library.gnome.org/devel/menu-spec/")

---

