---
title: "learning unity"
date: 2017-06-09
forum: Desktop Environments
---

### Post by Skaperen on 2017-06-09
i want to learn how to create custom launch buttons in unity.  for example i have a button to launch the terminal program but would like to launch two different terminal profiles.  in another case i want to launch a script of my own (which will set up a special environment).  i also want to give these buttons a custom appearance.  what documentation would be the best starting point to learn this?  any terminology i could google for?

---

### Post by again? on 2017-06-09
Documentation is [**HERE**]("https://standards.freedesktop.org/desktop-entry-spec/latest/index.html")
Create your launchers in **~/.local/share/applications**
If you want to modify a current launcher, copy it from **/usr/share/applications** to **~/.local/share/applications**
Launchers in ~/.local/share/applications will overide the default ones.

Here is an example of a launcher I use to run some of my own scripts.
```
[Desktop Entry]
Version=1.0
Name=Scripts
Exec=xdg-open /home/glen/scripts
Type=Application
Icon=/home/glen/Documents/coloured_folders/scripts-folder.png
Comment=My personal scripts
StartupNotify=false

# This sets the order of the Quicklist. Must match the [Desktop Action xxxxxxx]
Actions=Background;Cursor;ClockToggle;getip;poker-fix;Ping;Speed;Screensaver;zsync;Test.txt;Test Script;RunTest;Steam;TooltipToggle;Upper2lower;Vivaldi-Hooks-Fix;separator;edit-launcher;


[Desktop Action Background]
Name=Background Reset   
Exec=/home/glen/scripts/background-reset-gradient.sh
OnlyShowIn=Unity
StartupNotify=false

[Desktop Action Whatismyip]
Name=Whatismyip
Exec=/home/glen/scripts/whatismyip
OnlyShowIn=Unity

[Desktop Action zsync]
Name=Sync Daily Iso
Exec=altyo -e  "/home/glen/scripts/zsync.sh"
OnlyShowIn=Unity

[Desktop Action Test.txt]
Name=Test.txt
Exec=xdg-open "/home/glen/test.txt"
OnlyShowIn=Unity

[Desktop Action Cursor]
Name=Change Cursor
Exec=gnome-terminal --geometry 100x34+303+176 -e "/home/glen/scripts/change-cursor-trusty"
OnlyShowIn=Unity

[Desktop Action Test Script]
Name=Test Script Edit
Exec=xdg-open /home/glen/scripts/aatest.sh
OnlyShowIn=Unity

[Desktop Action altyo-fix]
Name=Altyo Fix
Exec=/home/glen/scripts/altyo-fix.sh
OnlyShowIn=Unity

[Desktop Action Screensaver]
Name=Screensaver  OFF/ON
Exec=/home/glen/scripts/toggle_screen_blanking.sh
OnlyShowIn=Unity

[Desktop Action Notes]
Name=Notes
Exec=xdg-open "/media/Data/Notes"
OnlyShowIn=Unity

[Desktop Action open-command]
Name=Open command in Terminal
Exec=/home/glen/scripts/xsel-terminal.sh
OnlyShowIn=Unity;

[Desktop Action RunTest]
Name=Test Script Run
Exec=gnome-terminal -e "/home/glen/scripts/aatest.sh"
OnlyShowIn=Unity

[Desktop Action ClockToggle]
Name=Clock-Toggle
Exec=/home/glen/scripts/toggle-clock.sh
OnlyShowIn=Unity

[Desktop Action TooltipToggle]
Name=Tooltip-Toggle
Exec=/home/glen/scripts/tooltips-toggle-trusty.sh
OnlyShowIn=Unity

[Desktop Action Brightness]
Name=Brightness
Exec=/home/glen/scripts/brightness.py
OnlyShowIn=Unity

[Desktop Action Reboot]
Name=XP Reboot
Exec=/home/glen/scripts/Reboot_to_Windows
OnlyShowIn=Unity

[Desktop Action WallChanger]
Name=WallChanger Random
Exec=/home/glen/scripts/wallpaper-changer-compiz-cube.sh
OnlyShowIn=Unity

[Desktop Action separator]
Name=______________________________________
Exec=
OnlyShowIn=Unity;

[Desktop Action edit-launcher]
Name=Edit Launcher
Exec=gedit /home/glen/.local/share/applications/MyScripts.desktop
OnlyShowIn=Unity;

[Desktop Action Ping]
Name=Ping Test
Exec=/home/glen/scripts/pingtest.sh
OnlyShowIn=Unity

[Desktop Action Speed]
Name=Speed Test
Exec=/home/glen/scripts/speedtest.sh
OnlyShowIn=Unity

[Desktop Action Upper2lower]
Name=Upper to Lower
Exec=/home/glen/scripts/upper2lower.sh
OnlyShowIn=Unity

[Desktop Action Vivaldi-Hooks-Fix]
Name=Vivaldi-Hooks Fix
Exec=altyo -e "/home/glen/scripts/vivaldi-hooks-fix.sh"
OnlyShowIn=Unity

[Desktop Action getip]
Name=Get-IP Loop
Exec=sh -c "killall get-ip-loop.sh; sleep 2 && /home/glen/scripts/get-ip-loop.sh"
OnlyShowIn=Unity

[Desktop Action Steam]
Name=Steam Environment-Toggle
Exec=/home/glen/scripts/game-settings.sh
OnlyShowIn=Unity

[Desktop Action poker-fix]
Name=Poker Fix
Exec=altyo -e "/home/glen/scripts/pokerth-sound-fix.sh"
OnlyShowIn=Unity
```
[ATTACH=CONFIG]275562[/ATTACH]


And another which overrides the default gedit launcher.
```
[Desktop Entry]
Name=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=false
MimeType=text/plain;
Icon=gedit
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.22.0
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport.sh
Keywords=Text;Editor;Plaintext;Write;
X-Ubuntu-Gettext-Domain=gedit

NoDisplay=true

DBusActivatable=false
Actions=new-window;new-document;addnote;addpackages;speedtest;Notes;

[Desktop Action new-window]
Name=New Window
Exec=gedit --new-window

[Desktop Action new-document]
Name=New Document
Exec=gedit --new-document

# my custom entries
[Desktop Action addnote]
Name=Add to Notes
Exec=/home/glen/scripts/add-to-notes.sh

[Desktop Action Notes]
Name=Notes
Exec=gedit /media/Data/Notes

[Desktop Action addpackages]
Name=Add Packages to Notes
Exec=/home/glen/scripts/add-packages-to-notes.sh

[Desktop Action speedtest]
Name=Speedtest results
Exec=gedit /home/glen/.speedtest
```
[ATTACH=CONFIG]275563[/ATTACH]

The pics will appear different than Unity as I'm using gnome-shell which supports Unity quicklists.

A launcher just to run a script can be as simple as
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=/home/glen/Documents/icons/translate2.png
Name=Translatify
Exec=/home/glen/scripts/translatify.sh
```

---

### Post by Skaperen on 2017-06-10
i copied /usr/share/applications/gnome-terminal.desktop to ~/.local/share/applications/philshell.desktop and added an option to the gnome-terminal command to use a specified profile.  i am guessing that i can add a button for this the same way as i added the first terminal, originally ... search for the application and drag it over to the left.  but the search failed to find "philshell".  how do i make the button now appear?  is there a file where unity keeps this list so i can automate adding it for all my other users?

---

### Post by again? on 2017-06-10
Show me your philshell.desktop file and I'll test.
If you want the launcher to be available system wide, place it in /usr/share/applications/.
This post may be helpful which shows how to add a .desktop file to the unity launcher with a command.
[https://ubuntuforums.org/showthread.php?t=2142675&p=12640956#post12640956](https://ubuntuforums.org/showthread.php?t=2142675&p=12640956#post12640956)

---

### Post by Skaperen on 2017-06-10
here is **[FONT=courier new]~/.local/share/applications/philshell.desktop[/FONT]**:

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;cmd;
TryExec=gnome-terminal
Exec=gnome-terminal --window-with-profile=one
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.18.3
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity;
Actions=New
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal --window-with-profile=onewide
OnlyShowIn=Unity

```

md5: 66db907647980f3de680e5a9c89f9770

and here is what i have for **[FONT=courier new]/usr/share/applications/gnome-terminal.desktop[/FONT]**:
in my Ubuntu 16.04.2

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;cmd;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.18.3
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity;
Actions=New
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
OnlyShowIn=Unity

```

md5: 3c27491e665946c1842f0658c4c68f0d

---

### Post by again? on 2017-06-10
I used your file and copied to ~/.local/share/applications/philshell.desktop
I changed the "Name=" so as not to conflict with other files.
```
[Desktop Entry]
Name=**Terminal[COLOR="#FF0000"]1[/COLOR]** 
```

I made philshell.desktop executable which will then show the "Name" in the file browser.
Logged out and back in and "Terminal1" shows up in an application dash search.
The file can then be draggged and dropped to the unity launcher.

---

### Post by Skaperen on 2017-06-11
looks like making it executable is not needed.   it's almost working for me now.   the next problem is the option does not seem to set the profile name.  it might be deleting the option.  and **[FONT=courier new]gnome-terminal[/FONT]** is not a file; it is a directory with 2 files.  the path name seen in "**[FONT=courier new]ps awx|grep term[/FONT]**" is **[FONT=courier new]/usr/lib/gnome-terminal/gnome-terminal-server[/FONT]**.  the man page for **[FONT=courier new]gnome-terminal[/FONT]** is not helpful about this.   i'll go do some more *googling*, now that i got this far.

---

### Post by again? on 2017-06-11
Doing something like you described above I would just copy /usr/share/applications/gnome-terminal.desktop without renaming.
```
cp /usr/share/applications/gnome-terminal.desktop ~/.local/share/applications/
```

Then edit to add a quicklist item.
```
gedit ~/.local/share/applications/gnome-terminal.desktop
```
```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;cmd;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.20.2
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity7;
Actions=new-window;[COLOR="#FF8C00"]onewide[/COLOR]
X-Ubuntu-Gettext-Domain=gnome-terminal

X-AppStream-Ignore=true

[Desktop Action new-window]
Name=New Terminal
Exec=gnome-terminal

[Desktop Action [COLOR="#FF8C00"]onewide[/COLOR]]
Name=Terminal Onewide
Exec=gnome-terminal --window-with-profile=onewide
```
Save and make executable
```
chmod +x ~/.local/share/applications/gnome-terminal.desktop
```
**gnome-terminal --window-with-profile=onewide** doesn't create a profile.
It loads an existing profile.
```
glen@Xen2:~$ gnome-terminal --window-with-profile=**notexist**
Profile 'notexist' specified but not found. Attempting to fall back to the default profile.
```

---

### Post by Skaperen on 2017-06-11
i want a button on the left side to open a fully wide terminal window and another button to open a half wide terminal window, not a command, although i am not opposed to running them through scripts.  then i will click the half-wide-terminal button when i want 2 terminals side by side (the font size i use lets me have 82 columns in each on my 1920x1080 pixel display).

---

### Post by again? on 2017-06-11
> **Skaperen said:**
> i want a button on the left side to open a fully wide terminal window and another button to open a half wide terminal window, not a command, although i am not opposed to running them through scripts.  then i will click the half-wide-terminal button when i want 2 terminals side by side (the font size i use lets me have 82 columns in each on my 1920x1080 pixel display).
If you look at post #2 in the first code block I have a quicklist item
```
[Desktop Action Cursor]
Name=Change Cursor
Exec=gnome-terminal --geometry 100x34+303+176 -e "/home/glen/scripts/change-cursor-trusty"
OnlyShowIn=Unity

```
You can specify the terminal geometry and position and optionally run a command with the **-e** flag.

You can find a geometry to your liking by positioning a terminal and then run
```
xwininfo
```
then click in the terminal to show current values.

---

### Post by Skaperen on 2017-06-12
to get terminal geometry within the terminal i have this Python code:

```
#!/usr/bin/env python3
import fcntl, struct, termios
width, height = struct.unpack('4H',fcntl.ioctl(0,termios.TIOCGWINSZ,struct.pack('4H',0,0,0,0)))[1::-1]
print( repr(width), 'x', repr(height) )

```

---

### Post by again? on 2017-06-12
> **Skaperen said:**
> to get terminal geometry within the terminal i have this Python code:

```
#!/usr/bin/env python3
import fcntl, struct, termios
width, height = struct.unpack('4H',fcntl.ioctl(0,termios.TIOCGWINSZ,struct.pack('4H',0,0,0,0)))[1::-1]
print( repr(width), 'x', repr(height) )

```
Use whatever you like. :P
xwininfo gives you position and size and can be copy and pasted directly into **gnome-terminal --geometry**.

---

### Post by Skaperen on 2017-06-12
i finally got 2 different profiles running.  i had to create the 2nd profile then exit all terminal windows.  turns out even starting different profiles runs all terminal windows from a single process.  once i had windows in different profiles i could size them as desired.

---

### Post by again? on 2017-06-12
Are you trying to get separate launcher icons to control different terminal profiles?

---

