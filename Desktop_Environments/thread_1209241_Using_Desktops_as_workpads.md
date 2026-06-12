---
title: "Using Desktops as workpads"
date: 2009-07-10
forum: Desktop Environments
---

### Post by BillGrates on 2009-07-10
Greetings. I have searched for a solution without finding.
I can use the four desktops from the bottom tray but what I would like to do is to have each desktop with a plain, but different background, as a workpad.
To provide the ability to be able to quickly launch applications from icons, select images or text, design etc. from each desktop.
Each desktop being unique to the others and used by different applications.

Is that possible please?

Using Ubuntu Jaunty 9.04 and also using UbuntuStudio 9.04.

Any help would be MOST appreciated.
Thanking you for any help/advice.

Please forgive my lack of experience if I have committed a sin/broken rules in posting.

---

### Post by Peter09 on 2009-07-10
Here is a link 

[http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

---

### Post by BillGrates on 2009-08-01
Peter thank you for your reply. Please excuse the delay with a reply I have a somewhat serious medical condition currently.
On one PC using Ubuntu 8.4 the system freezes when trying to configure CompizConfig.
On a second PC with Ubuntu Jaunty 9 installed the configuration seems to work but a cube does not show.
Restarting the PC the original default wallpaper remain.
I do NOT have a 3-D video card.
I do not use any applications requiring 3-D.
What I am trying to do is have selectable different desktop wallpapers that can be used as small working photo albums.
To use the selectable wallpaper as a workpad/work area. 
Do I require a 3-D video card?
Will ComPiz Fusion provide the answer to my selectable wallpaper photo album solution?
Please let me thank you again Peter (how do I send you a 'thank-you' bean?

---

### Post by antiram on 2009-08-02
the wallpaper switching is easy with wallpapoz
[http://ubuntuforums.org/showthread.php?t=468557](http://ubuntuforums.org/showthread.php?t=468557)

switch other things with a script. i use first workspace for general use with unhidden panels, second for win xp rdesktop session with hidden panels and third workspace for mythtv.
```

#! /usr/bin/python

import gtk
import gconf
import wnck

#for metacity and other
def workspace_changed(screen,previously_active_space):
    current_workspace = screen.get_active_workspace()
    wk_nr = current_workspace.get_number()
    set_workspace_properties(wk_nr)

#for compiz
def viewport_changed(screen):
    current_workspace = screen.get_active_workspace()
    x_Pos = current_workspace.get_viewport_x()
    wk_nr = x_Pos/screen.get_width()
    set_workspace_properties(wk_nr)
  
#set properties for workspace number with 0 based index  
def set_workspace_properties(workspace_number):
    client = gconf.client_get_default()
    if workspace_number==1:
        print "xp workspace"
        client.set_bool("/apps/panel/toplevels/top_panel_screen0/auto_hide", True)
        client.set_bool("/apps/panel/toplevels/bottom_panel_screen0/auto_hide", True)
        client.set_int("/apps/panel/toplevels/top_panel_screen0/unhide_delay", 500)
    elif workspace_number==2:
        print "mythtv workspace"
        client.set_bool("/apps/panel/toplevels/top_panel_screen0/auto_hide", True)
        client.set_bool("/apps/panel/toplevels/bottom_panel_screen0/auto_hide", True)
        client.set_int("/apps/panel/toplevels/top_panel_screen0/unhide_delay", 0)
        #client.set_string("/desktop/gnome/background/picture_filename", "/usr/share/backgrounds/feisty-final-ubuntu.png")
    else:
        print "other workspace"
        client.set_bool("/apps/panel/toplevels/top_panel_screen0/auto_hide", False)
        client.set_bool("/apps/panel/toplevels/bottom_panel_screen0/auto_hide", False)
        #client.set_string("/desktop/gnome/background/picture_filename", "/usr/share/backgrounds/simple-ubuntu.png")

screen = wnck.screen_get_default()
screen.force_update()
screen.connect("active_workspace_changed", workspace_changed)
screen.connect("viewports_changed", viewport_changed)

gtk.main()

```
save as WorkspaceSettings.py or so, make it executable with
chmod +x WorkspaceSettings.py

and make it automatically starting after login in System->Settings->Startup Programs or session programs or so

works with compiz and metacity, You can find the paths and values to set with gconf-editor.
e.g. background switching:
path=/desktop/gnome/background/picture_filename
value=/usr/share/backgrounds/simple-ubuntu.png

---

### Post by sidewalkcynic on 2009-08-02
when I terminal, I got```
--14:42:43--  http://wallpapoz.akbarhome.com/files...-0.4.1.tar.bz2
           => `files...-0.4.1.tar.bz2'
Resolving wallpapoz.akbarhome.com... 208.97.190.113
Connecting to wallpapoz.akbarhome.com|208.97.190.113|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:42:43 ERROR 404: Not Found.

```

Anyway, I found another wallpaper app in synaptic, 'wallpaper tray,' that just changes the wallpaper at specified intervals, which is enough for me - but I screwed up backgrounds trying to get it to designate a directory.

I mistakenly designated /usr/share/gnome-background properties, looking for /usr/share/background, and it flickered and didn't do anything; and so I rebooted. Now I cannot control the wallpaper/background all, and it uses the custom splash as a desktop background.:confused:

The app doesn't seem to take to any directory I give it.

I cannot, even, change system> preferences> appearence

---

### Post by sidewalkcynic on 2009-08-02
So, I removed the wallpaper tray app in synaptic, but still have problems.

When starting up the desktop flickers window, tha looks like a Nautilus browser window with no words or icons. I still cannot adjust preferreances - the window opens for a half second then closes. My Gnome sticky notes does not stay open when selecting a new note.

here is a copy of the ubuntu-wallpapers.xml file that I must have hooked up to to with the wallpaper tray app that caused the problem
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/heron-simple.png</filename>
    <options>zoom</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Elephant</name>
    <filename>/usr/share/backgrounds/simple-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#dab082</pcolor>
    <scolor>#dab082</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
</wallpapers>
```

---

