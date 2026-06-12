---
title: "Edit desktop context menu in lubuntu?"
date: 2014-01-02
forum: Desktop Environments
---

### Post by stinkeye on 2014-01-02
I've installed lubuntu-desktop in 13.04 and am trying to find the location to copy the default 
desktop menu (/usr/share/lubuntu/openbox/menu.xml) to my home folder so I can edit without root.

Tried to copy to... 
[LIST]
[*]~/.local/share/lubuntu/openbox 
[*]~/.config/lxsession/openbox 
[*]~/.config/lxsession/ubuntu
[*]~/.config/openbox
[/LIST]

I have placed an altered menu.xml in each of these locations and ran reconfigure but
menu remains as from **/usr/share/lubuntu/openbox/menu.xml **

---

### Post by vasa1 on 2014-01-02
I don't use the "right-click anywhere on the desktop" menu and so could be wrong. But I get the impression that the menu you want is now within **~/.config/openbox/lubuntu-rc.xml** and that that is the only thing you need to edit as a normal user for that user. In my original "lubuntu-rc.xml" in Lubuntu 13.10, the section is this (including the comments):
```
    </context>
  </mouse>
  <menu>
    <!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->
    <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
    <file>/usr/share/lubuntu/openbox/menu.xml</file>
    <file>menu.xml</file>
    <hideDelay>200</hideDelay>
    <!-- if a press-release lasts longer than this setting (in milliseconds), the
       menu is hidden again -->
    <middle>no</middle>
    <!-- center submenus vertically about the parent entry -->
    <submenuShowDelay>100</submenuShowDelay>
    <!-- time to delay before showing a submenu after hovering over the parent
       entry.
       if this is a negative value, then the delay is infinite and the
       submenu will not be shown until it is clicked on -->
    <submenuHideDelay>400</submenuHideDelay>
    <!-- time to delay before hiding a submenu when selecting another
       entry in parent menu
       if this is a negative value, then the delay is infinite and the
       submenu will not be hidden until a different submenu is opened -->
    <applicationIcons>yes</applicationIcons>
    <!-- controls if icons appear in the client-list-(combined-)menu -->
    <manageDesktops>yes</manageDesktops>
    <!-- show the manage desktops section in the client-list-(combined-)menu -->
    <showIcons>yes</showIcons>
    <!-- show icons on the menu -->
  </menu>
  <applications>
    <!--

```
For me, it starts at line 808 and ends at 835.

In some ways, Lubuntu doesn't provide a "default" Openbox experience and so you don't need to edit a separate menu.xml. (Just to be clear *this* menu.xml has nothing to do with the menu of lxpanel.)

---

### Post by vasa1 on 2014-01-03
My previous post maybe meaningless if you're in an Openbox session and not in a Lubuntu session :(

---

### Post by stinkeye on 2014-01-03
From what I understand, the **~/.config/lubuntu-rc.xml** just sets how the menu.xml behaves and sets the location ....**/usr/share/lubuntu/openbox/menu.xml**
It also states the custom location as **$HOME/.config/openbox/**.
But when I place a menu.xml in **$HOME/.config/openbox/** it does not override **/usr/share/lubuntu/openbox/menu.xml**.

I've freshly installed lubuntu 13.10.

---

### Post by vasa1 on 2014-01-03
How do you log in? Openbox session or Lubuntu session?

And it is ~/.config/openbox/lubuntu-rc.xml. I left out "/openbox"!

---

### Post by vasa1 on 2014-01-03
I just tried a Lubuntu session (after a long time) and I can't figure out how to get the Openbox menu to show up by clicking on the desktop :(

Let's hope someone who knows how will turn up!

---

### Post by stinkeye on 2014-01-03
Run ....
```
pcmanfm --desktop-pref
```
and select under advanced tab.

If I log into the openbox session the file placed at **~/.config/openbox/menu.xml** overides the default menu.
Doesn't work in the lubuntu session so I'm trying to find the right location for the menu.xml in my home directory when running a lubuntu session.

---

### Post by stinkeye on 2014-01-06
Ok found the solution.
In the Lubuntu session, the file ~/.config/openbox/lubuntu-rc.xml determines the location of the menu.xml to use.

Rclick desktop > advanced > show menu from window manager.
Can also run **pcmanfm --desktop-pref**.

Right click on the desktop will now show the Lubuntu menu from** /usr/share/lubuntu/openbox/menu.xml**

The openbox session menu is @ **/etc/xdg/openbox/menu.xml**
Copy the openbox menu to **~/.config/openbox/menu.xml** so you can edit without root.
```
cp /etc/xdg/openbox/menu.xml ~/.config/openbox
```

Edit **~/.config/openbox/lubuntu-rc.xml** to point to ~/.config/openbox/menu.xml
```
leafpad ~/.config/openbox/lubuntu-rc.xml
```
Search for "default menu file" 

You will see a section...
    ```
<!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->
    <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
    <file>[COLOR="#FF0000"]/usr/share/lubuntu/openbox/menu.xml[/COLOR]</file>
```


Change  
```
/usr/share/lubuntu/openbox/menu.xml
```
to
```
$HOME/.config/openbox/menu.xml
```
Save and close.

From the right click desktop menu choose reconfigure and you should now see the menu used in the openbox session.

Because your in the Lubuntu session the Exit command is different.
This is my  **~/.config/openbox/menu.xml** with the exit command edited.
```
<?xml version="1.0" encoding="UTF-8"?>

<openbox_menu xmlns="http://openbox.org/"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://openbox.org/
                file:///usr/share/openbox/menu.xsd">

<menu id="root-menu" label="Openbox 3">
  <item label="Terminal emulator">
    <action name="Execute"><execute>x-terminal-emulator</execute></action>
  </item>
  <item label="Web browser">
    <action name="Execute"><execute>x-www-browser</execute></action>
  </item>
  <!-- This requires the presence of the 'menu' package to work -->
  <menu id="/Debian" />
  <separator />
  <menu id="client-list-menu" />
  <separator />
  <item label="ObConf">
    <action name="Execute"><execute>obconf</execute></action>
  </item>
  <item label="Reconfigure">
    <action name="Reconfigure" />
  </item>
  <item label="Restart">
    <action name="Restart" />
  </item>
  <separator />
  [COLOR="#FF0000"]<item label="Exit">
    <action name="Execute">
      <command>**lxsession-default quit**</command>
    </action>
  </item>[/COLOR]
</menu>

</openbox_menu>
```

---

