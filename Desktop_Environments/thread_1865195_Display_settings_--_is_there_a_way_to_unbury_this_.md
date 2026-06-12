---
title: "Display settings -- is there a way to unbury this tool?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by yelvington on 2011-10-19
One of the many really irritating changes in Oneric is the relocation of the video display settings tool into the "System Settings" control panel. 

Is there a way to get it out? To access it directly?

I have an external monitor plugged into my laptop as a second display. I constantly have to reset my video settings because Ubuntu can't keep it straight when I suspend the computer. I also do a lot of presentations, plugging into various projectors. I need easy/fast access to the display settings. 

Under previous versions of Ubuntu, I could make the display tool available in the menu bar (systray). Now I have to dig three layers deep. This sucks.

Is there some third-party solution to this UI mess?

---

### Post by haqking on 2011-10-19
> **yelvington said:**
> One of the many really irritating changes in Oneric is the relocation of the video display settings tool into the "System Settings" control panel. 

Is there a way to get it out? To access it directly?

I have an external monitor plugged into my laptop as a second display. I constantly have to reset my video settings because Ubuntu can't keep it straight when I suspend the computer. I also do a lot of presentations, plugging into various projectors. I need easy/fast access to the display settings. 

Under previous versions of Ubuntu, I could make the display tool available in the menu bar (systray). Now I have to dig three layers deep. This sucks.

Is there some third-party solution to this UI mess?

Drag it to your dock, thats what the dock is for

see attached for an example from my virtual machine

---

### Post by yelvington on 2011-10-23
Let me try asking this question another way.

From digging around in the system, I know that **"gnome-control-center"** brings up the control panel that includes applets for various system settings.

I know that it's theoretically possible to invoke "gnome-control-center" with arguments that cause a specific setting tool to activate.

I want the "Displays" tool to open. How do I do that? From a command line? That will let me create a launcher that I can put in the Panel.

I'm not running Unity, Dash, or the Dock, and I will not ever run Unity so long as it resembles what I see today, and/or continues to rip menus away from windows. 

I'm running Gnome Classic, which isn't really Gnome 2 after installing the fallback package. I'm trying to restore as much system functionality as possible. I really regret having "upgraded" Ubuntu to Oneric, but what's done is done.

---

### Post by Larkspur on 2011-10-23
The command you're looking for is ```
gnome-control-center display
```

---

### Post by yelvington on 2011-10-23
Much better, thanks. To complete the fix:

[LIST]
[*] Alt-right click on the Panel, choose "Add to Panel"
[*] Choose "Custom Application Launcher"
[*] Name the launcher anything you want. Whatever you type will display when you mouseover the icon.
[*] Put the command *gnome-control-center display* in the command box. 
[*] In the comment box, place your favorite snarky comment about Unity. Or not.
[*] Click on the icon and change it to **/usr/share/icons/Humanity/apps/48/gnome-display-properties.svg**. This restores the familiar "monitor with the yellow triangle" icon.
[*] OK to save.
[/LIST]

One more bit of damage repaired.

---

