---
title: "Menus"
date: 2013-09-16
forum: Desktop Environments
---

### Post by Richard_Wegner on 2013-09-16
I am wondering if there is a way to change what it says for Menu...I have it where I click a button saying My Stuff (like the Windows START menu), it then gives me the types of files there are, and then from there I can load up a specific file.  Currently for my Browsers it has it just listed as Web Browser (within the Internet menu).  Is there a way I can change that to be the specific name of my browser?  I would like my Firefox to be stated as FireFox and my Chromium as Chromium NOT just as Web Browser.  I would like to also delete duplicate ones...for instance I have SNEX9X inside my Games Menu AND my System menu.  I would like it to be just in my Games one.  Also what if I want to create a new Menu how can I do it?

I am using XFCE 4.10 with Ubuntu 13.04 :)  Thanks for any help.

---

### Post by vasa1 on 2013-09-16
I think the answer lies in understanding .desktop files. These files are normally in /usr/share/applications and editing them requires administrative privileges. If you copy over the ones you wish to "play" with to ~/.local/share/applications, you won't need **sudo**. Also, the files in the latter location won't change each time your application is updated.

To give you a simple example, look in /usr/share/applications with your file manager. You should (I hope) see a file called **Thunar Settings**. If you run **ll /usr/share/applications** from your terminal, the same file will appear as **thunar-settings.desktop**. Copy this file over to ~/.local/share/applications. Here are its contents:

```
[Desktop Entry]
Version=1.0
Name=Thunar Settings
Comment=Configure the Thunar file manager
Exec=thunar-settings
Path=
#Icon=system-file-manager
Icon=/usr/share/icons/hicolor/24x24/apps/Thunar.png
Terminal=false
NoDisplay=false
Type=Application
Categories=Settings;XFCE;GTK;DesktopSettings;X-XFCE-SettingsDialog;X-XFCE-PersonalSettings
StartupNotify=true

```

While "thunar-settings.desktop" maybe it's "real" name, **both the file manager and your menu** will use the "friendlier" version as entered after **Name=** in the code above. If you wish to change the "friendlier" version to something more meaningful to you, just edit **Name=Thunar Settings** (in ~/.local/share/applications) to what you wish.

Here's some more reading:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
[http://askubuntu.com/a/282187/25656](http://askubuntu.com/a/282187/25656)

---

### Post by Richard_Wegner on 2013-09-17
Actually that is not I was referring to: here's a link to what I mean
[http://www.doctorvell.com/screen.jpg](http://www.doctorvell.com/screen.jpg)

Where it says Web Browser I want one to say Firefox and the other one say Chromium, etc...

---

### Post by vasa1 on 2013-09-17
> **Richard_Wegner said:**
> Actually that is not I was referring to: here's a link to what I mean
[http://www.doctorvell.com/screen.jpg](http://www.doctorvell.com/screen.jpg)

Where it says Web Browser I want one to say Firefox and the other one say Chromium, etc...
Yes. IMO, I've given you the solution.

---

### Post by SantaFe on 2013-09-17
Have you tried right clicking on your menu button & clicking on Properties & seeing if Show generic application names is check-marked?  If it is, try un checking it and you should see the correct titles.

Middle pic is the Applications menu, First Pic is with Show generic application names not checked, third pic is with it check-marked.  (I uploaded them in order, don't know why it's messed up.) ;)

---

### Post by Frogs Hair on 2013-09-17
You can create new menus and move items to it  via the main menu, but I don' t know about changing the existing category names.

---

### Post by Richard_Wegner on 2013-09-17
Fixed and thanks :)

---

### Post by fixitmanarizona on 2013-09-19
404 error to that link. website does not exist.
Do you use Xubuntu or are you simply using the minimalist environment XFCE?
Under Xubuntu just use "menu editor" in the main menu list under "system." 
It's really easy!
In the XFCE menu it looks like you can also change them to whatever you wish, but unchecking the generic names box seems easiest. AND there's an easy option there to change button name (I have my User Name there.)
More complicated, I also changed the graphics, my "start button" has the windows logo from XP. (conversely, I changed my XP start menu to have Tux on it, just to confuse people!) (Yes, it's a dual boot machine.)

---

