---
title: "Adding app to dock, Ubuntu 17.10 running Gnome"
date: 2017-11-02
forum: Desktop Environments
---

### Post by septantrionalis on 2017-11-02
I have an application (waterfox) unzipped and untarred in my home directory.  How do I add it to the dock.  I can't seem to figure this out.  When I start the app up and right click on it, I don't get that "add to favorites" selection as I do with apps listed in the "show applications" area.

---

### Post by dev-t on 2017-11-02
you need a file named waterfox.desktop
look in /usr/share/applications for a sample

---

### Post by deadflowr on 2017-11-02
Create a desktop file for it:
Basics on how to here:
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
Though the link is stated for unity, it's the same method.

Save the file to your ~/.local/share/applications directory in order for it to show in the menu.
(The .local share directory is hidden so if using a text editor like gedit (Ubuntu's default) then when saving right click on the main window area of the save as dialog box (which should list your folders and files), and select the right click option Show hidden files and folders then scroll till you find the .local entry and so on)

Hope it helps
... or makes sense

---

### Post by septantrionalis on 2017-11-03
Thanks.  The link actually helped.  I noticed the .desktop file already  existed in ~/.local/share/applications, but it still didn't show up in  the search.  I used desktop-file-install to copy the file to the /usr/share/applications directory.  The application still didn't show up when I did a search.  However, when I clicked on the icon through nautilus, I got a dialog box asking if I wanted to trust the application, which I did.  I was then able to right click on the application in the dock to add it to my favorites.

---

### Post by monkeybrain20122 on 2017-11-03
Works here. I put the .desktop file in ~/.local/share/applications.** Did you make your .desktop file executable? (right click it, Properties > Permissions > Allow execute) if not it won't show up in dash.**

This is my .desktop file, which is a straight forward modification of Firefox's I put my waterfox folder in /home/mb/opt (the archve unzipped to  waterfox-linuxxxx/waterfox, I take out the inner waterfox folder and place it in /home/mb/opt and delete the outer one, modify it according to your own set up) 
```

[Desktop Entry]
Version=1.0
Name=Waterfox Web Browser
Comment=Browse the World Wide Web
GenericName=Web Browser
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=/home/mb/opt/waterfox/waterfox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/mb/opt/waterfox/browser/icons/mozicon128.png
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=new-window;new-private-window;

[Desktop Action new-window]
Name=Open a New Window
Exec=/home/mb/opt/waterfox/waterfox -new-window

[Desktop Action new-private-window]
Name=Open a New Private Window
Exec=/home/mb/opt/waterfox/waterfox -private-window
```

---

### Post by stevecoh1 on 2018-05-09
Should this still work in Ubuntu 18.04?

I have 
[FONT=Courier New][Desktop Entry]
Version=4.7.3a
Name=Eclipse
Comment=Eclipse Oxygen-JEE
Exec=/home/scohen/eclipse-oxygen-jee/eclipse/eclipse
Icon=/home/scohen/eclipse-oxygen-jee/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=Developer;Application;

It does not appear.  Is logout or reboot necessary?  The file is executable.
[/FONT]

---

### Post by Dennis N on 2018-05-09
'Developer' isn't a valid Main category. It should be 'Development'. Changing that may help get it to appear in menus and dock(?) provided all the rest is ok.

---

### Post by monkeybrain20122 on 2018-05-09
> **stevecoh1 said:**
> Should this still work in Ubuntu 18.04?

I have 
[FONT=Courier New][Desktop Entry]
Version=4.7.3a
Name=Eclipse
Comment=Eclipse Oxygen-JEE
Exec=/home/scohen/eclipse-oxygen-jee/eclipse/eclipse
Icon=/home/scohen/eclipse-oxygen-jee/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=Developer;Application;

It does not appear.  Is logout or reboot necessary?  The file is executable.
[/FONT]

Not sure if just making  it executable is enough "new gnome".  Try launch it by clicking  it once and at the pop up that warns you about untrusted .desktop file  just click launch anyway. As another ridiculous hoop you seem to have to go through this ritual rather than just chmod +x in this latest iteration of gnome shell in order for the .desktop file to work.

---

