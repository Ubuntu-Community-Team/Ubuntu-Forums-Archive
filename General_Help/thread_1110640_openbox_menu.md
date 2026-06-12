---
title: "openbox menu"
date: 2009-03-30
forum: General Help
---

### Post by GujuLvr on 2009-03-30
i m trying to create a pipemenu
this is what i have on menu.xml

```
<menu execute="openbox-xdgmenu /etc/xdg/menus/applications.menu" id="gnome" label="Application"/>
```

if i just execute this in terminal openbox-xdgmenu /etc/xdg/menus/applications.menu it generate this output

```
<openbox_pipe_menu>
<menu id="xdg-menu-Accessories" label="Accessories">
<item label="Bulk Rename">
<action name="Execute"><execute>/usr/lib/thunar/ThunarBulkRename   </execute></action>
</item>
<item label="Calculator">
<action name="Execute"><execute>gcalctool</execute></action>
</item>
<item label="Character Map">
<action name="Execute"><execute>gucharmap</execute></action>
</item>
<item label="Disk Usage Analyzer">
<action name="Execute"><execute>baobab</execute></action>
</item>
<item label="Manage Print Jobs">
<action name="Execute"><execute>system-config-printer-applet --no-tray-icon</execute></action>
</item>
<item label="Passwords and Encryption Keys">
<action name="Execute"><execute>seahorse</execute></action>
</item>
<item label="Take Screenshot">
<action name="Execute"><execute>gnome-screenshot --interactive</execute></action>
</item>
<item label="Terminal">
<action name="Execute"><execute>gnome-terminal</execute></action>
</item>
<item label="Text Editor">
<action name="Execute"><execute>gedit   </execute></action>
</item>
<item label="Thunar File Manager">
<action name="Execute"><execute>Thunar   </execute></action>
</item>
<item label="Tilda">
<action name="Execute"><execute>tilda</execute></action>
</item>
<item label="Tomboy Notes">
<action name="Execute"><execute>tomboy --search</execute></action>
</item>
<item label="Tracker Search Tool">
<action name="Execute"><execute>tracker-search-tool</execute></action>
</item>
</menu>
<menu id="xdg-menu-Games" label="Games">
<item label="AisleRiot Solitaire">
<action name="Execute"><execute>/usr/games/sol</execute></action>
</item>
<item label="Blackjack">
<action name="Execute"><execute>/usr/games/blackjack</execute></action>
</item>
<item label="Chess">
<action name="Execute"><execute>/usr/games/glchess</execute></action>
</item>
<item label="Five or More">
<action name="Execute"><execute>/usr/games/glines</execute></action>
</item>
<item label="Four-in-a-Row">
<action name="Execute"><execute>/usr/games/gnect</execute></action>
</item>
<item label="FreeCell Solitaire">
<action name="Execute"><execute>/usr/games/sol --freecell</execute></action>
</item>
<item label="Gnometris">
<action name="Execute"><execute>/usr/games/gnometris</execute></action>
</item>
<item label="Iagno">
<action name="Execute"><execute>/usr/games/iagno</execute></action>
</item>
<item label="Klotski">
<action name="Execute"><execute>/usr/games/gnotski</execute></action>
</item>
<item label="Mahjongg">
<action name="Execute"><execute>/usr/games/mahjongg</execute></action>
</item>
<item label="Mines">
<action name="Execute"><execute>/usr/games/gnomine</execute></action>
</item>
<item label="Nibbles">
<action name="Execute"><execute>/usr/games/gnibbles</execute></action>
</item>
<item label="Robots">
<action name="Execute"><execute>/usr/games/gnobots2</execute></action>
</item>
<item label="Same GNOME">
<action name="Execute"><execute>/usr/games/same-gnome</execute></action>
</item>
<item label="Sudoku">
<action name="Execute"><execute>/usr/games/gnome-sudoku</execute></action>
</item>
<item label="Tali">
<action name="Execute"><execute>/usr/games/gtali</execute></action>
</item>
<item label="Tetravex">
<action name="Execute"><execute>/usr/games/gnotravex</execute></action>
</item>
</menu>
<menu id="xdg-menu-Graphics" label="Graphics">
<item label="F-Spot Photo Manager">
<action name="Execute"><execute>f-spot</execute></action>
</item>
<item label="GIMP Image Editor">
<action name="Execute"><execute>gimp-2.6   </execute></action>
</item>
<item label="OpenOffice.org Drawing">
<action name="Execute"><execute>ooffice -draw   </execute></action>
</item>
<item label="XSane Image Scanner">
<action name="Execute"><execute>xsane</execute></action>
</item>
</menu>
<menu id="xdg-menu-Internet" label="Internet">
<item label="Ekiga Softphone">
<action name="Execute"><execute>ekiga</execute></action>
</item>
<item label="Evolution Mail">
<action name="Execute"><execute>evolution --component=mail</execute></action>
</item>
<item label="Firefox Web Browser">
<action name="Execute"><execute>firefox   </execute></action>
</item>
<item label="Pidgin Internet Messenger">
<action name="Execute"><execute>pidgin</execute></action>
</item>
<item label="Remote Desktop Viewer">
<action name="Execute"><execute>vinagre   </execute></action>
</item>
<item label="Terminal Server Client">
<action name="Execute"><execute>tsclient</execute></action>
</item>
<item label="Transmission BitTorrent Client">
<action name="Execute"><execute>transmission   </execute></action>
</item>
</menu>
<menu id="xdg-menu-Office" label="Office">
<item label="Dictionary">
<action name="Execute"><execute>gnome-dictionary</execute></action>
</item>
<item label="Evolution Mail and Calendar">
<action name="Execute"><execute>evolution</execute></action>
</item>
<item label="OpenOffice.org Presentation">
<action name="Execute"><execute>ooffice -impress   </execute></action>
</item>
<item label="OpenOffice.org Spreadsheet">
<action name="Execute"><execute>ooffice -calc   </execute></action>
</item>
<item label="OpenOffice.org Word Processor">
<action name="Execute"><execute>ooffice -writer   </execute></action>
</item>
</menu>
<menu id="xdg-menu-Sound & Video" label="Sound & Video">
<item label="Audio CD Extractor">
<action name="Execute"><execute>sound-juicer   </execute></action>
</item>
<item label="Brasero Disc Burning">
<action name="Execute"><execute>brasero   </execute></action>
</item>
<item label="Movie Player">
<action name="Execute"><execute>totem   </execute></action>
</item>
<item label="Rhythmbox Music Player">
<action name="Execute"><execute>rhythmbox   </execute></action>
</item>
<item label="Sound Recorder">
<action name="Execute"><execute>gnome-sound-recorder</execute></action>
</item>
</menu>
<separator /> 
<item label="Add/Remove...">
<action name="Execute"><execute>/usr/bin/gnome-app-install</execute></action>
</item>
</openbox_pipe_menu>

```


however i get nutthing from openbox menu.

---

### Post by kerry_s on 2009-03-30
i think you need 2 parts.

the menu and the command.

```
<menu id="ID" label="Applications" execute="script" />

script:
<openbox_pipe_menu>
  <item label="Applications">
    openbox-xdgmenu /etc/xdg/menus/applications.menu
  </item>
</openbox_pipe_menu>

```

see here: [http://icculus.org/openbox/index.php/Help:Menus#Syntax](http://icculus.org/openbox/index.php/Help:Menus#Syntax)

---

### Post by GujuLvr on 2009-03-31
i think it create syntax error when openbox try to execute,  Audio & Video, & is invalid character. i guess that is the reason why it doenst genrate. but anyway. i wann have gnome meny like. system, adminstrator opeiton and all that not jst Asscories, Audio & video. etc..

---

### Post by kerry_s on 2009-03-31
you can always do it the old fashion way, with a text editor or obmenu. in xml " & " is " &amp; " , doesn't always work though. never got it to work in labels="Audio &amp; Video", i used " + " instead.

i know what you mean i did the gnome look in jwm, you might find a screenshot around the forums, now i'm just back to simple, just moved it all to 1 menu. i do mine manually with a text editor.

---

### Post by TechZilla on 2011-04-24
Apparently, currently at this time, the script still doesn't work because ubuntu has a category with a "&" in it.

I have had some luck with [OpenBox-Menu](http://mimasgpc.free.fr/openbox-menu_en.html)

at least openbox-menu is xdg and somewhat better then the very obsolete "menu" package method. that debian menu method needs to be depreciated already, it is just so damn easy to set up.  The results however are fairly horrible...they are usable, just hideous.


BTW, suggesting manually editing the xml is a non-solution, and fairly obvious. It would be preferable (IMO), to keep to keep those "your method is difficult and I don't know about it, so just give up" suggestions to oneself.   (not trying to to offend)

---

