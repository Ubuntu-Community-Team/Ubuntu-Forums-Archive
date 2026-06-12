---
title: "Can't install theme correctly!!!"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by Redrazor39 on 2008-02-02
I want to install this theme and get all the orange looks and panel customizations: [http://mariuxv.deviantart.com/art/Hardy-Theme-75628261](http://mariuxv.deviantart.com/art/Hardy-Theme-75628261)

but all I can get to work is the title bar! I downloaded the gz then extracted to tar then extracted to regular folder (or something) and then I read the readme and made it an emerald theme. I can only get the title bar working. Here is a copy of the readme:
§ sudo aptitude install gtk2-engines-murrine
then copy "Hardy-Mariux" in your /home/.themes directory
Go in System -> preferences -> themes to choose this gtk theme
To install the icons, just untar "icons_gusty_ubuntu.tar.gz" into your /home/.icons directory and then select them in theme manager.

	*Wallpaper
Make a right click on your Desktop, and enter in the menu "change your wallpaper".

        *Emerald
Just double click on the file.

        *GDM Theme
Open System->Administration->Login Window
Go to "Local", clic Add, then select the tar.gz file, OK, then select Mariux Glossy Hardy.


	*Compiz Fusion Settings

Just open "Advanced Desktop Effects Settings"-> Preferences-> Profile-> Import 
then select "Mariux.profile" into the Hardy-Mariux/Compiz Fusion Settings directory

Thanks to:
petercui for the wallpaper
Zgeg for the icons

There is no such directory as /home/.themes or /home/.icons anywhere! I'm on that first step (already tried the emerald one, but that didn't work all the way) and I don't know how to do it the other ways!) just click the link at the beginning of the post and take a look at the theme. Please help me! I'm a super n00b at this stuff and have only had ubuntu for a week!:confused:

---

### Post by shutslar on 2008-02-02
I don't think the author meant /home/.icons or /home/.themes literally.  Try this to see these folders:

Open a new terminal and type:  ls -a

OR
[LIST]
[*]From the menu click:  Places > Home Folder
[*]When the folder window opens, click the menu options:  View > Show Hidden Files
[/LIST]

This will display these hidden directories.  I beleive the author of the instructions probably meant to place those files in YOUR home directory under these hidden directories.

Hope this helps

---

### Post by Vadi on 2008-02-02
If there's a dot before the folder name, that means it's hidden. Try pressing Ctrl+H in nautilus to toggle hidden folders :)

---

### Post by Redrazor39 on 2008-02-03
thnx. Okay, I copied Hardy-Mariux (reg. folder) into my .themes folder, but now how do I make this theme work completely? when using emerald I can get the titlebars right but I can't get the panels or orange windows right! How do I do this?:confused:

---

### Post by Vadi on 2008-02-03
Try going to system - preferences - appearance. I think the first tab that opens there is where you pick themes.

---

### Post by Redrazor39 on 2008-02-03
that doesn't really work... I can't even find this hardy theme on that.

---

### Post by Redrazor39 on 2008-02-03
come on ppl! I can only get the titlebars working and sometimes that's buggy! Can someone reword these instructions in the first post in SUPER N00B terms so that I can understand it? include steps for every little thing so I won't screw up! The panels and interior windows aren't getting the right colors!! please helP~

---

### Post by Redrazor39 on 2008-02-04
I thought people helped a lot here! What's going on?

---

### Post by Tenken on 2008-02-04
Extracting the Files:
1. Download the .gz file to your desktop
2. Right-click the .gz file and select the "extract here" option to get the .tar file
3. Right-click the .tar file and select the "extract here" option to get the normal Hardy-Mariux folder

Installing the emerald theme
1. Open the Hardy-Mariux folder on your desktop, open the Hardy-Mariux folder inside it
2. Open the Emerald folder inside it
3. Open System->Preferences->Emerald Theme manager
4. Drag the .emerald file into the Emerald theme manager

Installing the GDM theme
1. Open the Hardy-Mariux folder on your desktop, open the Hardy-Mariux folder inside it
2. Open the GDM Folder
3. Open System->Administration->Login Window, enter your password, click the "local"tab
4. Drag the Glossy Mariux.tar.gz file into the theme window
5. Click "install" to install the theme
6. Click the radio button next to the newly installed theme.

Installing the GTK theme
1. Open a terminal and type
```
sudo apt-get install gtk2-engines-murrine
cd ~
cp Desktop/Hardy-Mariux/Hardy-Mariux/GTK/Haryd-Mariux ~/.themes
```
2. Go System->Preferences->Appearance->Theme tab
3. Click "customize"
4. Click the "control" tab and select the Hardy-Mariux theme

Installing the Icons
1. Open a terminal and type
```
cd /Desktop/Hardy-Mariux/Hardy-Mariux/Icons
tar -zxvf icons_gutsy_ubuntu.tar.gz
mv icons_ubuntu_gutsy ~/.icons
```
2. Go System->Preferences-Appearance->Theme tab
3. Click "customize"
4. Click the "icons" tab and select the new gutsy icon theme

---

### Post by Redrazor39 on 2008-02-05
Whoa, thanks! that's just what I was asking for! Lemme try it out first lol

---

### Post by tjacobs on 2008-05-18
I am having problems with this theme too. The controls work fine, the window decorations are fine (using emerald), the icons are fine, but the window colors are not being set. By the way, with sudo apps, everything is working fine. Is it possible I've got cruft left over from something I've done in the past with themes that is preventing the colors from displaying?

---

