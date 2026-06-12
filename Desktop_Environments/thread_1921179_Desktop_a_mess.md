---
title: "Desktop a mess"
date: 2012-02-06
forum: Desktop Environments
---

### Post by Jonners59 on 2012-02-06
I am running 11.10 64-bit desktop edition with all the latest updates installed and an nVidea video card.  I use two screens in an extended desktop view.  I.e. they are side by side and show a wide screen.

I upgraded from 11.04 to 11.10 and had a screen warning every time I booted up, but after clicking the OK button all was always fine, so did little about it.

I decided last week to try and resolve the problem and whilst the problem has gone, I have completely messed up my desktop and the more I search and try the worse it gets!!!!!!!!!!!!

It should be noted that I am not a Unity fan - certainly not as it stands and so have the Gnome panels install and the Unity Launcher only.

The symptoms:
Gnome launchers:
The Desktop Manager icon only shows one desktop and can not be changed
Open applications do not show in the panel

Windows:
Some applications do not have a title bar and so have no "controls"
Some - Chrome do, but the drop down menus nothing can be selected.  I.e. "menu - Quit", though Ctrl+Q works
Some applications, the window is stuck in the top left corner and can not be moved.
Some the application has no controls and can not be moved, so not even shut down
Force Quit does not work (new version for Unity)
I seem to have more than one desktop
Evolution, I can not change the size and it is too big - goes off the screen
Some apps hog the desktop  by forcing themselves to the top so other apps underneath can not be reached

Cursor:
is a X in some apps, like Evolution
And when writing messages, there is no cursor...

Screenshot enclosed:
note the two desktops - I was able to move them apart.  The upper having the desktop icons.
Note too that the "System" windo can not be closed
Firefox alos has no menu, close and minimise in the toolbar

Argh, a mess!  [COLOR="Red"]**[FONT="Arial Black"][SIZE="4"]ANy help PLEASE!?!?!?!??!?!?[/SIZE][/FONT]**[/COLOR]:cry::cry:

---

### Post by jj97403 on 2012-02-06
i don't know if this will help, but you can try...............

uninstall your nvidia proprietary drivers, and any other proprietary video drivers, and just go with the default video driver ubuntu 11.10 used at install?

the last couple days i was having a really hard time setting up an extended monitor -- dual (or mirror) worked fine -- but i couldn't get extended through my ati/amd graphics card controller or ubuntu 11.10 display settings.

so i just uninstalled the ati/amd graphic drivers that i activated after install and went with the default video drivers. i'm not exactly sure what they are because when i run 'system settings' > 'additional drivers' it is not displaying that i have any proprietary video drivers activated, but the default settings must be using some graphic driver because i'm in Unity and i'm in hi-def with two different size & resolutions on each monitor, not to mention one is hdmi and the other vga.

---

### Post by Jonners59 on 2012-02-06
Cheers
I'll try that if I get my kids of my work PC tonight, or else tomorrow AM.

---

### Post by jj97403 on 2012-02-06
I meant to say "deactivate," not uninstall.

System Settings > Hardware > Additional Drivers > and then just deactivate any drivers that are activated.

Reboot, and then the Ubuntu 11.10 default is installed. It doesn't say what it is, nor does it say what (if any) graphic driver is actually activated, but something is installed by default.

Then System Settings > Hardware > Displays > and tweak from there.

I was able to download linux software & controller for my ati/amd graphic driver, but it did not play nice with Unity, nor could I assign different resolutions on each monitor. However, once I rolled back to the default graphic driver and only worked within Ubuntu 11.10's System Settings > Displays, I had a lot more control and was able to do everything I wanted.

Incidentally, I'm in Unity UI, not 2d. Also using 64 bit 11.10.

---

### Post by Jonners59 on 2012-02-07
Did this.  No change, though I now can not control which screen my panels go.

New screenshot

It was fine before I tried to remove the alert message, which I have done.

Anyone.  Any more ideas??????

---

### Post by Jonners59 on 2012-02-08
I ran unity panel from terminal and got this when it launched.....

[HTML]indicator") 
unity-panel-service: no process found
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-homebutton.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-panel-service: no process found
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "F10" 
unity-2d-panel: [CRITICAL] Wnck: wnck_window_is_maximized: assertion `WNCK_IS_WINDOW (window)' failed
unity-2d-panel: [CRITICAL] Wnck: wnck_window_is_maximized: assertion `WNCK_IS_WINDOW (window)' failed
[/HTML]

Does it help?

---

### Post by Jonners59 on 2012-02-09
Resolved:

Removed:
Workspaces
Unity
Window Manager Tweaks

Rebooted, it made no difference

Re-installed all the above then installed
GWorkspace
xfce-4

Rebooted

Selected xfce from the login options (the little cog in the login password window) and it all worked.  Yes, it is a different desktop, but actually I have best of all worlds now.  I have my old panels back and Unity panels and launchers and all is diggety dandy.

I am certain the problem was caused by Unity removing the controls for the windows and in some cases hiding the Menus under panels.

---

