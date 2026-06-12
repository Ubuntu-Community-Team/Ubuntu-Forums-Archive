---
title: "standard desktop, no desktop icons or menus activate"
date: 2009-05-02
forum: Desktop Environments
---

### Post by ChinFurr on 2009-05-02
I've installed ubuntu 9.04 NBR on my new eee pc 1000HE. The hardware seems to be working fine, however when I switched from the cluttered desktop to standard there is an issue with the actual desktop. USB connected hardware and items in my ~/Desktop folder do not show up. Also if I right-click on the desktop the context menu that lets you change backrounds, create folders etc. also does not show up. I have disabled maximus, is there another NBR utility that may be responsible, a setting I can check or is this a bug?

Any advice would be greatly appreciated.

---

### Post by psyopper on 2009-05-11
Not a bug I don't think, but I'm not a dev either.

I have this same issue. I installed UNR on my Mini 9 but didn't like the "clutter" so I removed Maximus and Netbook-Launcher from my session... err... startup programs. I can see the desktop background but I cannot interface with it - no context menu on right click, no icons, etc.

I noticed in gconf that apps->nautilus->preferences->show_desktop was unselected. I selected it and logged back in, but that did not resolve the issue.

Any help out there?

---

### Post by Fingers &amp; Thumbs on 2009-05-11
Chinfurr, did you disable the nbr desktop using the "switch desktop mode" utility in preferences? I've just tried that and everything worked fine for me. Simply uninstalling maximus and netbook launcher as psyopper has done is likely to cause problems since no instruction has been invoked to replace the utilities that the standard desktop uses; of course this can be fixed by invoking them manually and adding to startup, but unfortunately it is so long since i played around with these things that i can't remember what the neccessary programs are called.

  I'll have a little dig to see if i can refresh my memory.

---

### Post by psyopper on 2009-05-12
That actually worked.

Alt-F2 to open the Run Application window and enter Netbook-Launcher

Preferences - Switch Desktop Mode

Dropped me back to the standard interface with an interactive desktop. Thanks!!

The downside is that it defaulted the theme back to the standard Ubuntu theme with white tool bars, etc. Now I guess it's time to go back through and hack out black tool bars with white text.

---

### Post by ChinFurr on 2009-05-14
When I did originally switch I used the Preferences -> switch desktop modes, however reselecting as stated above did seem to fix it. Guess some kind of hickup...

---

### Post by luptinpitman on 2009-06-23
Yep, switching from classic desktop to ubuntu netbook desktop and then back to classic desktop via the Switch Desktop Mode app fixed it for me.  Icons back and desktop again right clickable.

---

### Post by Nexer on 2009-06-24
i have tried pressing alt F2 on the desktop and i get nothing, i can still right click and menus work but i have no visable toolbars

---

### Post by luptinpitman on 2009-06-24
> **Nexer said:**
> i have tried pressing alt F2 on the desktop and i get nothing, i can still right click and menus work but i have no visable toolbars

Try running the Netbook-Launcher (or netbook-launcher) from a terminal.  Don't have my Ubuntu machine available to verify.

---

### Post by Nexer on 2009-06-25
the only way i can access a terminal is via ctrl+alt+f2 and that takes up the whole screen like (removes all the gui)
 
and when i type sudo netbook-launcher i get "Gtk-WARNING **: cannot open display" 
 
is there a way of creating a launcher for terminal (note im using acer aspire one)

---

### Post by jsauder2 on 2009-06-26
I am having the same problem as Nexer. Any help would be much appreciated.

---

### Post by jsauder2 on 2009-06-26
I just found a temporary solution. If you right click on your desktop and select "create launcher" and then put "gnome-terminal" in the command box, you will be able to launch a terminal from the desktop. Once you launch a terminal, if you type "gnome-panel" you should get your panels back.

I don't think this will repair the problem, but it will get the panels back. If you change to Ubuntu Netbook Desktop mode before shutting down or restarting, you should be able to start up normally.

---

### Post by mjmsyth on 2009-06-26
@jsauder2

Many thanks for that. Just around about the time you posted your message, I managed to mess up my install of NBR by switching desktops and to put it mildly, my head was melted. I feared having to reinstall everything!

Once again, thanks a lot.

MJ

---

### Post by alpha-buntu on 2010-01-02
Hello,

I was using Netbook Remix 9.10. I deinstalled all that fancy netbook remix menue, launcher, maximus and so on... 

After that, I have a empty desktop with no right-click menue! 

In 9.10, ubuntu has removed the possibility via a tool to comfortably switch back to a normal desktop.

so how can I get back a normal desktop?

---

### Post by D_Wahl on 2010-01-11
I'm having the same issue as things seem to have changed from 9.04 to 9.10.  Course I only realized this after an hour of saying "I swore I did this before..." and searching all through the menus and forums...

it would be great for deployment if I can use the same image for my 1-3rd graders as I can for the 4-5 graders and just allow them to have different desktop environments.

---

### Post by JohnE1 on 2010-01-11
If you can get to a terminal, follow the instructions below to use GNOME's configuration tool, gconf-editor, to turn on/off the desktop icons, system icons, and any other desktop settings you want to modify.

TIP: Keep a record of the settings you change and a copy of these instructions.

From my experience, each user's settings are separate.

1. Login on the account you want to modify and open a terminal/console window.

2. At the term/console prompt, enter: gconf-editor &

3. To display the desktop icons, navigate to and add a checkmark to:

/apps/nautilus/preferences/show_desktop

4. The computer, home, network, trash, and volumes icons can each be displayed or hidden separately.

To turn those icons on/off vavigate to:

/apps/nautilus/desktop/

and a checkmark to the following icons you want to display:

/apps/nautilus/desktop/computer_icon_visible
/apps/nautilus/desktop/home_icon_visible
/apps/nautilus/desktop/network_icon_visible
/apps/nautilus/desktop/trash_icon_visible
/apps/nautilus/desktop/volumes_visible

To see the changes, you might have to log out of GNOME and log back in. 

You'll have to repeat these steps for each user.

If you still don't see your changes, login as root, turn on/off all the same settings you set for your users, then log out of GNOME and log back in.

Snoop around and you'll find a lot of GNOME's settings can be controlled via the configuration tool, gconf-editor.

Good Luck!!

John

---

### Post by shahniaz on 2010-01-12
HI, I have installed ubuntu 9.1, but i dont see any icons at desktop in GUI mode, When i check through terminal it shows, but by desktop is blank. I tried creating shortcuts at desktop but it does not appear. Kindly help

---

### Post by shahniaz on 2010-01-12
> **JohnE1 said:**
> If you can get to a terminal, follow the instructions below to use GNOME's configuration tool, gconf-editor, to turn on/off the desktop icons, system icons, and any other desktop settings you want to modify.

TIP: Keep a record of the settings you change and a copy of these instructions.

From my experience, each user's settings are separate.

1. Login on the account you want to modify and open a terminal/console window.

2. At the term/console prompt, enter: gconf-editor &

3. To display the desktop icons, navigate to and add a checkmark to:

/apps/nautilus/preferences/show_desktop

4. The computer, home, network, trash, and volumes icons can each be displayed or hidden separately.

To turn those icons on/off vavigate to:

/apps/nautilus/desktop/

and a checkmark to the following icons you want to display:

/apps/nautilus/desktop/computer_icon_visible
/apps/nautilus/desktop/home_icon_visible
/apps/nautilus/desktop/network_icon_visible
/apps/nautilus/desktop/trash_icon_visible
/apps/nautilus/desktop/volumes_visible

To see the changes, you might have to log out of GNOME and log back in. 

You'll have to repeat these steps for each user.

If you still don't see your changes, login as root, turn on/off all the same settings you set for your users, then log out of GNOME and log back in.

Snoop around and you'll find a lot of GNOME's settings can be controlled via the configuration tool, gconf-editor.

Good Luck!!

John
i executed gcong-editor from terminal, but the config editor showed me blank root folder. i didnt get the option  /apps/nautilus/preferences/show_desktop

---

