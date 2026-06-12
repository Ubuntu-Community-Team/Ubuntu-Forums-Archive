---
title: "Gnome, gedit, custom desktop launchers and quicklists."
date: 2017-04-26
forum: Desktop Environments
---

### Post by again? on 2017-04-26
Transitioning to Ubuntu-gnome 17.04.
I have a number of custom desktop launchers using unity quicklists.
For the most part they work where my custom launchers  in ~/.local/share/applications override the default /usr/share/application launchers.
Can't get my custom gedit launcher to work though.

It has a couple of quicklist entries to launch copy and paste scripts.
When I drag and drop gedit from the dash to dock I get the default gedit icon and a 
duplicate immovable icon with my custom quicklists.
[ATTACH=CONFIG]274770[/ATTACH]
The custom quicklists work but then after a gnome-shell reload I'm left with only
the default icon and quicklists.
The custom quicklists are retained in Plank.
[ATTACH=CONFIG]274771[/ATTACH]

For testing I copied  /usr/share/applications/gedit.desktop to ~/.local/share/applications/gedit.desktop
```
cp /usr/share/applications/gedit.desktop ~/.local/share/applications/
```
Don't believe it's necessary but made the desktop file executable.
```
chmod +x ~/.local/share/applications/gedit.desktop
```
Same result even without editing the ~/.local/share/applications/gedit.desktop file.

Other custom launchers I use for Gnote and shutter don't have this problem.
What's with gedit?

---

### Post by again? on 2017-04-26
After reading this [bug]("https://bugzilla.redhat.com/show_bug.cgi?id=1235413") it appears the problem is "DBusActivatable=true".
Quicklist Actions need to comply to some GAction spec when dbus activation is used. ---> [https://www.bountysource.com/issues/8435261-dbusactivatable-flag-interferes-with-jumplist-actions](https://www.bountysource.com/issues/8435261-dbusactivatable-flag-interferes-with-jumplist-actions)

The solution that worked was to use the org.gnome.gedit.desktop file instead.
```
cp /usr/share/applications/org.gnome.gedit.desktop ~/.local/share/applications/
```

Edit the local file.
```
gedit ~/.local/share/applications/org.gnome.gedit.desktop
```

Changing 
```
DBusActivatable=true
```
to
```
DBusActivatable=false
```

For reference this is my ~/.local/share/applications/org.gnome.gedit.desktop with my [COLOR="#B22222"]custom changes[/COLOR].
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

[COLOR="#B22222"]DBusActivatable=false[/COLOR]
Actions=new-window;new-document;[COLOR="#B22222"]addnote;Notes;[/COLOR]

[Desktop Action new-window]
Name=New Window
Exec=gedit --new-window

[Desktop Action new-document]
Name=New Document
Exec=gedit --new-document

[COLOR="#B22222"]# my custom entries
[Desktop Action addnote]
Name=Add to Notes
Exec=/home/glen/scripts/add-to-notes.sh

[Desktop Action Notes]
Name=Notes
Exec=gedit /media/Data/Notes[/COLOR]
```

At first you still get 2 launcher icons but after a gnome-shell reload you are left 
with just the one launcher with your custom quicklist items.
Same method would probably work for other applications that use dbus activation.

---

### Post by deadflowr on 2017-04-26
Do they share the same name?
If they do, perhaps try renaming the quicklist one something like gedit2.desktop or something.

---

### Post by again? on 2017-04-26
Yes, the quicklists would work in a standalone custom launcher but would rather have them in my default gedit launcher.

---

