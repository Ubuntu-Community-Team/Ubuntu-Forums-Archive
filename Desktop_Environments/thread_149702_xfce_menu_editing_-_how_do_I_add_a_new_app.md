---
title: "xfce menu editing - how do I add a new app?"
date: 2006-03-24
forum: Desktop Environments
---

### Post by chugru on 2006-03-24
Hi, all...

I have just started using xubuntu and am trying to acquaint myself with xfce4. I wish someone would explain to me the process of adding a new application to the xfce menu and, also, where would I expect to find the icon that should accompany the application?

Sorry about such a lame question, but I am very new to this...:(

---

### Post by taurus on 2006-03-24
Do you plan to add to existing menu or do you want to create a new menu for your apps? 

Assuming you want to create a menu menu for all your apps.  Place a cursor to the right (or left) of the bottom panel and click the right button.  Pick "Add new item" (the first choice) -> Launcher.  You can use the default icons on the list if you want or you can browse to the new one that you have.  At the "Command:" field, just type in the name of the program you want to run, assuming it's in the path; otherwise, you need to complete the whole path.  And at the end, click "Attach menu to launcher" so you can add more stuff to the same menu later on.  Click "Close" to close it.  

Now, you will see your new menu with a triangle to the right of it.  If you ever want to add more items to the same menu, place a cursor over the triangle and click the left button -> Add launcher.

---

### Post by chugru on 2006-03-25
**taurus...**Thank you for responding!

Let me be more specific...

When I right click an open space of the xfce desktop, a menu of programs/applications opens. Into **that** menu, I would like to add a new application shortcut with its icon (e.g. **update-manager**).

KDE has a menu editor for this purpose, so I assume **Xfce4-MenuEditor** should be similar. When I open "default menu", however, I don't see all the same menu items displayed that I see with a mouse right click on the desktop, and I can't figure out how to add any items...

What am I missing, here??

Thanks...

---

### Post by simon_is_learning on 2006-03-25
there is a file caled menu.xml

locate it and start playing around =)

---

### Post by taurus on 2006-03-25
Wouldn't it be easier just to add that to the bottom panel?

---

### Post by chugru on 2006-03-25
[QUOTE=simon_is_learning]there is a file caled menu.xml

locate it and start playing around =)[/QUOTE]
...Found it and trying to understand it!

Instructions: ```
+ Applications:
   <app name="Name in menu" cmd="Command to run" term="false"
        icon="iconfile"  snotify="false" visible="true" />
   The 'term' attribute determines if the program needs a terminal to run,
   and 'snotify' sets whether or not the program supports startup
   notification.  You can set an icon to be displayed next to the item with
   the 'icon' attribute.  Only 'name' and 'cmd' are required.

```

The application I wish to launch as a menu item requires the command:```
sudo /usr/bin/update-manager
```

I think I am having a permissions problem, and I don't know how to run a command requiring root privileges from within the xfce menu...:???: 

Does anyone have any thoughts??

Thanks!

---

### Post by Ptero-4 on 2006-11-01
put 
```
gksu /usr/bin/update-manager
```
instead of
```
sudo /usr/bin/update-manager
```
And you'll be fine.

---

### Post by Wangsta on 2006-11-02
> **chugru said:**
> 
Instructions: ```
+ Applications:
   <app name="Name in menu" cmd="Command to run" term="false"
        icon="iconfile"  snotify="false" visible="true" />
   The 'term' attribute determines if the program needs a terminal to run,
   and 'snotify' sets whether or not the program supports startup
   notification.  You can set an icon to be displayed next to the item with
   the 'icon' attribute.  Only 'name' and 'cmd' are required.

```

so do you put this in the menu.xml file to add an application? 

anyway, how do you make the menu bigger? my menu is incredibly small (the icons and the text) and is almost impossible to read.

one more thing, how do i change the background color of the menu? can i give it rounded edges or make it semi-transparent?

---

### Post by Wangsta on 2006-11-03
bumpo

---

### Post by kerry_s on 2006-11-03
Can't you just right click the mouse icon and select menu editor?

Okay i booted into xfce4, it's settings> menu editor <or> right click the menu icon> menu editor <or> accessories appfinder> xfce4 menu editor <or> alt+F2 and type xfce4-menueditor <or> settings>settings manager>desktop>behavior>edit menu.

I don't see why you can't find the menu editor.

---

### Post by Wangsta on 2006-11-03
Of course I know about the menu editor.

The menu editor (as far as i know) only edits entrys, such as a seperator, a launcher, or a submenu.

but what I want to know is how to edit the text (font, size, color etc), the background color, the size of the icons, and just how large it is.

i'd also like to edit things like transparentness or giving the menu rounded edges.

---

### Post by kerry_s on 2006-11-03
Ohh, you want to get into the guts of it. LOL, there might be an easy way but we'll have to look into it more, in fluxbox i'm using a .gtkrc-2.0 file to set my settings, maybe that can be used to pass the kind of settings your looking for. It's just a simple hidden text file in your home directory. On mine i only have 2 settings for thunar. I'm sure with the right wording you can pass other settings. I'll google around and get back to you.

---

### Post by kerry_s on 2006-11-03
Never mind that text file, go to /usr/share/themes and grab the gtkrc for the theme your using and tweak that till you get the look your after, visit the xfce4 web site for enabling transparency.

---

### Post by Wangsta on 2006-11-05
When i change the size to bold and 12, it makes the menu bigger but it also makes firefox and all my other applications bigger too. and as you can see in the first picture, the size of the firefox text is larger than the menu, even after i made them both bold.

[with bold and size 12]("http://img97.imageshack.us/img97/5682/screenshotyr4.png")

what i really want is just to get the menu icons bigger. Like in Ubuntu, where the application list has lots of room, and great big icons.

i also can't tell which parts of the gtkrc change JUST the right-click menu...

---

### Post by Wangsta on 2006-11-05
this is how it is normally. the text is tiny and the icons are miniscule.
is there anyway to just make them bigger?

---

### Post by Magni on 2006-12-21
hello,
and how can i edit this submenu of menu.xml?
```

<include type="system" style="simple" unique="true" legacy="true"/>

```

---

### Post by Magni on 2006-12-22
> **Magni said:**
> hello,
and how can i edit this submenu of menu.xml?
```

<include type="system" style="simple" unique="true" legacy="true"/>

```

you find the answer here:
[http://ubuntuforums.org/showthread.php?t=193093](http://ubuntuforums.org/showthread.php?t=193093)

---

### Post by lmo on 2006-12-27
```
+ Applications:
   <app name="Name in menu" cmd="Command to run" term="false"
        icon="iconfile"  snotify="false" visible="true" />
   The 'term' attribute determines if the program needs a terminal to run,
   and 'snotify' sets whether or not the program supports startup
   notification.  You can set an icon to be displayed next to the item with
   the 'icon' attribute.  Only 'name' and 'cmd' are required.
```

Oh, I see. This is easier than freedesktop method.

First 
```
cp /etc/xdg/xfce4/desktop/menu.xml to ~/.config/xfce4/desktop/
```

Then, editing ~/.config/xfce4/desktop/menu.xml, I just stuck this under <app name="Web Browser" ...
```
	<app name="Thunderbird Email" cmd="/usr/local/firefox-downloaded/thunderbird/thunderbird" icon="/usr/share/pixmaps/thunderbird50.xpm"/>
```

Poof ... Thunderbird Email is under Web Browser on the menu.

Oh, cool ...
```
        <menu name="Internet" icon="/usr/share/pixmaps/tsclient/tsclient.png">
		<app name="Firefox Web Browser" cmd="xfbrowser4" icon="firefox"/>
		<app name="Thunderbird Email" cmd="/usr/local/firefox-downloaded/thunderbird/thunderbird" icon="/usr/share/pixmaps/thunderbird50.xpm"/>
       </menu>
```

---

