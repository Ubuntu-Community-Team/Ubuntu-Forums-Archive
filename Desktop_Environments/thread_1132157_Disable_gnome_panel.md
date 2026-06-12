---
title: "Disable gnome panel"
date: 2009-04-21
forum: Desktop Environments
---

### Post by celticbhoy on 2009-04-21
I want to disable gnome panel on my netbook and use awn exclusively, to free up much needed screen space. I would like to know how to disable it, but not completely remove it, just in case the dock starts acting up and I need to re-activate the panel. How do I go about this???

---

### Post by Tahakki on 2009-04-21
Go to your session thing (System->Preferences->Sessions) and kill the process gnome-panel. Then save the session.

I did that, but didn't like it. It makes it tricky to get at files. Should be okay on a netbook, though.

---

### Post by celticbhoy on 2009-04-21
Thats the thing, I am using Jaunty and in the System --> Preferances --> Startup Apps choice there is no mention of gnome-panel. So I was looking for another way to disable it.

---

### Post by Tahakki on 2009-04-21
They changed it? Maaan, you can't even disable processes now.

Why not try the netbook remix?

Sorry I wasn't much help . :P

---

### Post by celticbhoy on 2009-04-21
Thats ok thanx for the time.

I just hate netbook remix's.

---

### Post by wanchai on 2009-04-25
System->Preferences->Sessions doesn't exist any more either...

You can get rid of the panels in the following way:
[LIST]
[*]start gconf-editor
[*]in the tree structure, navigate to /desktop/gnome/session
[*]double click on the value "required_component_list"
[*]remove "panel" from the list that opens
[/LIST]

---

### Post by miramardesign on 2009-04-30
I have tried this but there doesn't seem to be a remove option in the new jaunty's gconf-editor (unless im missing it somehow) there only seems to be "unset key" and that doesn't do anything.

---

### Post by wanchai on 2009-05-01
For me it's the same on Intrepid and Jaunty. Please have a look at the attached screenshot, that should explain it a little better than words.

---

### Post by miramardesign on 2009-05-01
I did that but gnome-panel still re-launches after a sec and is enabled on startup.   Also gnome-panel is still visible if I click on the required_components folder in gconf....   see screenshot:confused:

---

### Post by wanchai on 2009-05-01
I suppose the 'panel' entry under required_components is not read when 'panel' is not included in required_components_list. I have removed 'panel' from the list, and also still have the panel->gnome-panel key. Logging out and logging in again was all that's needed. No more gnome-panel, just a minimalist awn.

However, if you ever had the option "automatically remember..." in gnome-session-properties aka 'Startup Applications' switched on you may have an entry referring to gnome-panel in ~/.config/gnome-session/saved-session. Keep this option off for now, clean out the saved-session directory and try again.

By the way, once you got rid of the gnome panels, and if you don't like the tray icons applet in awn, you may want to check out 'stalonetray'.

---

### Post by celticbhoy on 2009-05-02
How do you configure stalonetray, ie position & size. The notification area is the only thing that keeps me on AWN instead of cairo dock.

---

### Post by wanchai on 2009-05-03
Whenever I tried cairo dock, I always came back to AWN. But that's another topic, this thread is about getting rid of gnome-panel... ;-)

In order to start stalonetray, I have the following script in my Startup Applications (gnome-session-properties):

```

#!/bin/csh -f
sleep 20
stalonetray --transparent --window-layer bottom --icon-gravity SW >& /dev/null

```

This gives me a (fake) transparent icon tray in the lower left corner of the screen. The icon-gravity specifies in which direction icons are added inside the tray. window-layer=bottom tells it to always stay in the background. There are also geometry and icon-size parameters that let you position the tray elsewhere on the screen and modify the space available to each icon. Stalonetray has a man page that explains these and many more parameters.

The sleep is necessary because otherwise the session manager would start stalonetray at a point where the window manager and/or compiz aren't really ready to handle this app properly. Of course, you can experiment with the duration.

---

### Post by celticbhoy on 2009-05-03
Thanx for the advice, but I just upgraded to cairo-dock 2. It does just what I am after.

---

### Post by id10twork on 2009-05-03
why not just delete it? you can always easily add it back with ease at any time if you decide to not use awn solely anymore.

---

### Post by wanchai on 2009-05-03
id10twork, what do you mean by "just delete it"? Right-click on a panel and select "delete this panel"? That option is grayed out if you have only one panel left, so you cannot delete the last one.

Removing gnome-panel from the list of required components is (normally) just as easy and you can also add it back as easily. And you can also add it back temporarily by running gnome-panel from a terminal. Since you're not deleting anything in this case, the gnome-panel configuration will be kept and after starting it manually the panel(s) will look as before.

---

### Post by BazookaAce on 2009-05-19
Have you managed to hide the Gnome-panel? I did it 3 days ago, and here's how:

```
gconf-editor /apps/panel/toplevels/panel_1
```

"X" means ON.

Autohide [X]
Autohide Size **0**
Orientation: **Bottom**
Monitor **0**
Screen **0**
Size **0**
X **10000**
Y **10000**

Note: If this doesn't work, try this setup in /apps/panel/toplevels/top_panel

---

### Post by wanchai on 2009-05-20
What we were discussing here initially was how to get rid of the gnome panel completely, i.e. not to run it at all. This makes sense for people using a dock like awn which can replace the gnome panel.

Nevertheless, BazookaAce's post made me look into autohide again because I always wanted to use it on my non-Compiz machine where I cannot run awn, but never liked the way it looked. Now I figured out why it was ugly.

Have a look at the attachment, open it in Gimp or EOG (in EOG switch off "smooth images when zoomed"), then enlarge to 400% or so. The first line shows a bottom panel with property "Background = None (use system theme)". In this case, there are a one-pixel gray line and a one-pixel white line above the icons. When I switch to autohide with autohide size = 0 or 1, then a single white pixel line is drawn across the screen. Not that pretty, but ok.

In the second line I have switched the panel to an (ugly) solid color. Now these two extra pixel lines, some sort of 3-D effect, are gone, and the hidden panel looks weird because it shows the top row of the icons' pixels.

For the third line I switched the panel to mostly transparent (that was my normal setting). Here we still see that ugly top pixel row and this stopped me from using autohide.

Today I fiddled with my gtkrc again and added the following:
```

style "panel" {
  bg[NORMAL]     = "#360F03"
  fg[NORMAL]     = "white"
}

class "Panel*"          style "panel"
widget "*PanelApplet*"  style "panel"
widget "*PanelWidget*"  style "panel"
```

This recolors only the gnome panel, all the menu bars, etc, still have their original colors. Switching the panel properties back to none gives me the image shown in the fourth line. And that looks good to me. I picked a color that matches the average of my wall paper. People who use detailed images might have to fiddle a bit more...

Two more tweaks to the panel that make it nicer for me: enable_animation=off and unhide_delay=200

---

### Post by johnrizle on 2009-06-26
it feels safe to just hide than to remove it completely, if you are just after increasing screen size like me, then it serves the purpose

---

### Post by fabounet on 2009-06-26
right click on Cairo-Dock2 -> help
then, go to the section "how to replace the gnome-panel", and in the end, the solution to not launch th epanel at all (thus saving some ressources and startup time) is given ;)

---

### Post by Simian Man on 2009-06-26
If you want to do it simply, but dirtily, you could just:
```

sudo su
mv /usr/bin/gnome-panel /usr/bin/gnome-panelBACK
echo "" > /usr/bin/gnome-panel
chmod a+x /usr/bin/gnome-panel

```

To make the gnome-panel program do nothing at all.  If you want to revert, just move the gnome-panelBACK back to gnome-panel.

---

### Post by pedrogfrancisco on 2009-10-30
I went to
> gconf-editor /apps/panel/toplevels/panel_1
and set unhide_delay to 10000. If I leave the mouse cursor 10 seconds on the tray it will appear, and will not interfere with Gnome-Do's dock.

---

### Post by gregbzh on 2009-12-14
> **pedrogfrancisco said:**
> I went to

and set unhide_delay to 10000. If I leave the mouse cursor 10 seconds on the tray it will appear, and will not interfere with Gnome-Do's dock.
Thanks.  It's the only way that works for me.  Cheers.

---

### Post by newb85 on 2009-12-28
> **fabounet said:**
> right click on Cairo-Dock2 -> help
then, go to the section "how to replace the gnome-panel", and in the end, the solution to not launch th epanel at all (thus saving some ressources and startup time) is given ;)

This doesn't seem to work for me.  I was able to remove "panel" from the required components list, but after restarting, the panel would still restart if I killed it.  Then, I removed "gnome-panel" from the value of panel and restarted again.  Still, no change in behavior.  All other options seem blocked.  Any suggestions?

---

### Post by fabounet on 2009-12-30
write "cairo-dock" in the key, instead of "gnome-panel"
this is a bug in Gnome.

---

### Post by Mi11z on 2010-09-26
> **wanchai said:**
> System->Preferences->Sessions doesn't exist any more either...

You can get rid of the panels in the following way:
[LIST]
[*]start gconf-editor
[*]in the tree structure, navigate to /desktop/gnome/session
[*]double click on the value "required_component_list"
[*]remove "panel" from the list that opens
[/LIST]

You can also do it in a few clicks with ubuntu tweak. :D

---

