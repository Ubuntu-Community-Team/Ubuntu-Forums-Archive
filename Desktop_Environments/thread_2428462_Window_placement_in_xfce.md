---
title: "Window placement in xfce"
date: 2019-10-04
forum: Desktop Environments
---

### Post by amanchesterman on 2019-10-04
I have a Dell laptop computer running Xubuntu 18.04.3 with XFCE 4.12 and I'm puzzled by odd behaviour in the placement of newly-opened windows.

I like to run applications **not** maximised and I like all windows to be aligned to the top left corner of the workspace (just below the panel). When I open applications most windows behave in this way apart from 'Terminal' (xfce4-terminal) and 'File Manager' (Thunar). The behaviour I have observed is:
[LIST]
[*]If opened on an empty desktop, all apps (including Terminal and File Manager) align to the top left corner.
[*]If opened over an existing **maximised** window, all apps (including Terminal and File Manager) align to the top left corner.
[*]If opened over an existing **non**-maximised window, all apps **except** Terminal and File Manager align to the top left corner -- but Terminal and File Manager open aligned somewhat to the right and down ... I think maybe aligned to the bottom right corner?
[/LIST]

I'm puzzled by this behaviour and find it slightly annoying. How can I set all windows (including Terminal and File Manager) to align to the top left corner, all the time?

Thank you in advance for your assistance!

---

### Post by Skaperen on 2019-10-05
some commands use a "more sophisticated" search logic.  i believe xfce4-terminal prefers a larger open area over the corner.  this mat be built-in logic that can't be configured.  there may be command line options that can better control this.  i always open mine maximized and put each terminal in its own workspace.

---

### Post by egeezer on 2019-10-05
In earlier versions of Xfce there was an option in the Compositor section of Window Manager Tweaks to have windows open aligned to the vertical blank, i.e. to the right of the first vertical free space.  The option is no longer present in the GUI, but whether a similar function can be created through the terminal is a question way beyond my skill level.

---

### Post by amanchesterman on 2019-10-09
Just a couple of lines to thank you both for your input! I won't mark this as 'solved' because for me the issue remains; but your posts have convinced me that (a) I haven't missed an obvious solution in the Settings menu and (b) a proper solution would require technical fiddling that I'm not capable of. It's not a big problem anyway, I can live with it.
Thanks again, and good wishes to you.

---

### Post by Holger_Gehrke on 2019-10-09
I don't know how to set thunar (the xfce file manager) to a specific place, but xfce4-terminal accepts a '--geometry' option. Adding '--geometry +0+30' to the exec-line in the .desktop-file for xfce4-terminal puts the window on the left just below the panel I've got at the top of the screen. The full description of a geometry specification can be found in the manual page for X (man 7 X).

Holger

---

### Post by him610 on 2019-10-09
While using Xubuntu for years, I never thought much about initial windows placement when opening a program. This is what I have observed on a 29 inch wide monitor: Xfce4-terminal opens far right mid-height, mousepad lower far right, thunar lower far right, libreoffice lower right, chrome upper left under top panel. It is my belief the initial window placement of a program is based on the window placement of that program when last closed.

---

### Post by amanchesterman on 2019-10-11
Thank you both for your comments! To respond to you both in one post (I hope you don't mind):

Holger_Gehrke: I've tried your suggestion. (I'm focusing on Terminal for the time being, as you suggest.) I amended the .desktop file using your post and it made no difference. I checked the manual page you refer to and it says that the option is '-geometry' with one initial dash rather than two. I changed it to one dash and it still makes no difference. Opened on an empty desktop or over a maximised window, Terminal is aligned to the top left corner under the panel; opened over a non-maximised window it is displaced to the right and down, apparently aligned to the bottom right corner of the screen.

However, the man page explains:
"The  layout  of  windows on the screen is controlled by special programs called _window managers_. Although many window managers will honor geometry specifications as given, others may choose to ignore them."
So I am thinking that perhaps this is the explanation? Although the initial geometry for the Terminal window (the x and y offset) is specified in the .desktop file, the 'window manager' is ignoring it?

If so, can anyone tell me what the window manager for Xubuntu is? Are there settings I can control?

him610: You say that it's your belief that "the initial window placement of a program is based on the window placement of that program when last closed". Yes, that's exactly what I believed too! But I've learned that it's not so, at least not on my computer. If I have Terminal open aligned top left, and then close it, and then re-open it over a non-maximised window, it appears aligned bottom right; if I then close it in that position, and re-open it over a maximised window (or over an empty desktop), it appears aligned top left.

Of course you may not experience this behaviour on such a large screen as yours, but on a modest 15.5 inch diagonal laptop, that's what I experience.

Thanks again to all who have offered comments and suggestions!

---

### Post by Holger_Gehrke on 2019-10-11
I only mentioned 'man 7 X' for the complete specification of the argument to the '--geometry' option. The manual for xfce-terminal gives the option as '**--**geometry=*geometry*' with a note to read 'man 7 X' to find out how to specify a geometry. I've tried it from both a maximised and non-maximised terminal (starting a new terminal from a terminal) and from a desktop-file in the whisker-menu with the option '--geometry -0+30' (both with and without the '=' given in the man page) on an empty desktop, over a maximised window and on top of a couple of non-maximised windows and it **always** gave me a window sitting in the top-right corner (that's what the **mandatory** sign in the offset-part of a  geometry means: +=from top or left side, -=from bottom or right side). Do you perhaps use another terminal and not xfce-terminal ? You can check in "Menu"->"Settings"->"Preferred Applications"->Tab "Tools".

The standard Window-Manager for XFCE is xfwm4. It's configured through several (xml) files somewhere under /etc/xdg/ and ~/.config. All the settings I've seen in those can also be reached through the two settings tools ("Menu"->"Settings"->"Window Manager" and "Window Manager Tweaks" or 'xfwm4-settings' and 'xfwm4-tweaks-settings' in a shell) or from 'xfce4-settings-editor'. It is probably possible to use a different wm but I've never tried.

Window-sizing and placement is a slightly complicated topic. Some programs 'remember' their last size and position and ask the window manager (through the same mechanism used for '-geometry' or similar options) to set them up this way again. 

Holger

---

### Post by amanchesterman on 2019-10-13
Holger many thanks, I'm making some progress.

I followed your suggestion: I opened the terminal and then opened another terminal from the command line. When I entered
```
xfce4-terminal --geometry=50x70+0+30
```
it responded exactly as it should, i.e. a small terminal window opened at the top left corner, under the Panel, even over a non-maximised window. Great!

However when I put exactly the same command into the .desktop file, saved it, and then used the Whisker menu to open a terminal window, it ignored it.
So either the menu is ignoring the .desktop file or I have edited the wrong file ... or something else is going awry.

The desktop file I edited is /home/john/.local/share/applications/xfce4-terminal.desktop

Can you offer any further suggestion? Thank you for your help so far!

---

### Post by amanchesterman on 2019-10-13
OK I have made some more progress with this, I think.

I created a new entry for Terminal in the Whisker menu with the command: ```
xfce4-terminal --geometry=+0+30
```
It works perfectly: the terminal window opens top left under the Panel, whether or not the window underneath is maximised.

The existing (default) entry for terminal in the menu has a different command: ```
exo-open --launch TerminalEmulator
```
I assume this invokes whatever program is set as the default terminal, using the 'Preferred Applications' dialog in Xfce.

The root of the problem seems to be that there is no way to specify a command within the 'Preferred Applications' dialog, and that when ```
exo-open --launch TerminalEmulator
``` is invoked it ignores the .desktop file for xfce4-terminal -- which in my case includes the 'geometry' parameter.

As you say Holger, > window-sizing and placement is a slightly complicated topic. An understatement I think! At least I understand things better now, and I have a way to ensure that commands in the whisker menu open terminal where I want it.

I'll not mark this thread as 'solved' just yet, in case anyone wants to add further info about this topic or even to suggest how I can conrol the placement of the Thunar file manager as well ...?

---

### Post by Holger_Gehrke on 2019-10-13
> **amanchesterman said:**
> 
So either the menu is ignoring the .desktop file or I have edited the wrong file ... or something else is going awry.

The desktop file I edited is /home/john/.local/share/applications/xfce4-terminal.desktop


I think it's "something else", probably the name and the categories set for your desktop file; you probably have an additional entry for the Terminal somewhere in the menu now which does what you want and two or three generated from the old desktop file which don't. The name-field inside the desktop-file gives the applications an identity and the categories define the app's place in the menu. The .desktop-file that's installed by XUbuntu is /usr/share/applications/exo-terminal-emulator.desktop and has an Exec-line "exo-open --launch TerminalEmulator". I just right-clicked on the item in the menu and selected "Edit Application" (well, actually it said "Anwendung bearbeiten"; my system is set up in German ...) and got a small dialog in which I changed the command by just adding the option. That resulted in a new .desktop file which overruled the default one being written to ~/.local/share/applications with the change I made.

Holger

---

### Post by amanchesterman on 2019-10-18
As you say, I've now got a launcher in the menu which makes Terminal behave as I want -- thank you for all your help.
Now I just need to puzzle out how to do the same with Thunar. But I'm marking this as 'solved'.

---

### Post by vanadium on 2019-11-13
You can add the desired options after the "exo-open --launch TerminalEmulator" command, i.e., make that "exo-open --launch TerminalEmulator  --geometry=+0+30". The --geometry option will be passed to your favourite terminal emulator, which in your case (and in a default Xubuntu install) is xfce4-terminal.

Are you aware of the "Placement" tab in "Window Manager Tweaks? The slider determines the minimum window size for which "smart placement"  will be applied. Setting this to a minimum will apply smart placement for any opened window, setting it to max will revert to one of the default options listed further down, either opening centered, or placed under the mouse cursor. This will, however, only be in effect for applications that do not restore their own window settings.

Your best bet to take full control on window placement yourself may be using a tool such as devilspie and its successor devilspie2. That tool stays in memory and watches all windows that are created. When a window meets certain criteria, it is acted upon according to rules you define in a config file. Thus, you can automatically place windows on a certain position of the screen, on a certain workspace, have them automatically maximized, minimized or sized.

---

### Post by amanchesterman on 2019-11-16
Thanks for your post Vanadium!

I had looked at 'Window Manager Tweaks' but I couldn't see that it would do what I wanted. If only it offered the default option to open all windows 'aligned top left' it would be perfect. :D

I wasn't aware of devilspie2, thank you for pointing it out. As you say it offers total control of window placement. I may experiment with it when I have more time. Thanks again!

---

