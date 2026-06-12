---
title: "How to use Gnome, GDM, Icon, Cursor themes (and more)"
date: 2005-04-06
forum: Desktop Environments
---

### Post by WMCoolmon on 2005-04-06
I couldn't find a unified guide on how to actually *use* skins, and had to find stuff out from scattered threads on the forums. For future reference by me (When I forget something, which I know I will) and anyone else, I put together this guide.

I've based it on my experience with the stuff from [gnome-look.org](http://www.gnome-look.org ), which has lots of very nice themes (Some Ubuntu-specific).

--------------------------------------------------

**Notes:**
- Every time you see a dollar sign inside quotation marks, it means to enter that command from the console as it appears within the quoation marks. For example:
"$ ls -l"
- I assume you have the extra repositories ([http://ubuntuguide.org/temp/#extrarepositories](http://ubuntuguide.org/temp/#extrarepositories)) set up for this guide.

**Downloading and extracting to /usr/share/pixmaps**
Several times I say to download/extract something to /usr/share/pixmaps; you WILL need to use sudo or su. If you are queasy about the console, I recommend you download and extract the file to the desktop, then move files in the console with the following (Replace file_goes_here with the file you want to move):

*For all files but splash screen images*
1) "$ cd /usr/share/pixmaps"
2) "$ sudo mv ~/Desktop/file_goes_here ."
3) Repeat #2 for all extracted files

*For splash screens*
Splash screens are stored in their own special directory, so the commands are slightly different.
1) "$ cd /usr/share/pixmaps/splash"
2) "$ sudo mv ~/Desktop/file_goes_here ."
3) Repeat #2 for all extracted files

--------------------------------------------------

**GDM Themes**
1) Download the theme(s) to an easily accessible location
2) From the main menu, start System->Administration->Login Screen Setup
3) Make sure that the "Local:" field has "Graphical greeter" selected
4) Click the "Graphical greeter" tab
5) Click "Install new theme" and select the package
5) Repeat #4 for all themes you want to install
6) Double-click the theme you want to use
7) Click "close"
8) To see the new GDM screen, simply logout (No reboot required)

-------------------------

**Gnome splash screen**
1) Download and extract the icon to /usr/share/pixmaps/splash
2) Open the configuration editor (Main menu->System tools->Configuration editor)
3) Go to /apps/gnome-session/options and click on the folder.
4) Check "show_splash_screen"
5) Click twice, slowly, on the splash_image field and enter "splash/name_of_file", without quotes, replacing name_of_file with the name of the file WITH THE EXTENSION.
9) Close the Configuration Editor. To see the splash screen in action, log out and log back in to Gnome.

-------------------------

**GTK 2.0+ Themes**
1) Download the theme(s) to an easily accessible location
2) From the main menu, go to System->Preferences->Theme
3) Drag the compressed file into the list
4) Repeat #4 for all themes. Note that as you drag the themes in, a success message will appear that will tell you what exact type of theme was added.
5) To pick a main theme, simply click on it.
6) Once you've chosen a main theme, to pick a control or border theme, click the "Theme Details" and pick from the lists in the "Controls" or "Window borders" tabs. THe "Icons" tab will also let you select which icon set to use.

-------------------------

**Icon Themes**
1) Download the theme(s) to an easily accessible location
2) From the main menu, go to System->Preferences->Theme
3) Click "Theme details"
4) Select the "Icons" tab
5) Drag the compressed file into the list
6) Repeat #5 for all themes
7) Select a theme by clicking on it (Icons will update instantaneously)
8) Click "Close" when done

-------------------------

**Cursors**
1) Download the theme to an easily accessible location
2) If you haven't got gcursor, do "$ sudo apt-get install gcursor"
3) Start it with "$ gcursor"
4) Click 'Install theme' and select the compressed file to add it
Note that some cursor themes may come with multiple versions (ie left-handed); in this case, you will have to manually extract the folder with the version you want, then right-click and select "Create archive...", select tar.gz, and click "OK" before you can add it
5) Repeat #3 for all themes you want to install
6) Once you're finished, select the theme you want to use and click "Close"

-------------------------

**Individual Application Icons**
*Gnome menu icon*
1) Install the Gnome menu editor ([http://ubuntuguide.org/temp/#menu-editor](http://ubuntuguide.org/temp/#menu-editor))
2) Download & extract the icon to /usr/share/pixmaps
3) If the app is in the menu, use the menu editor to select the entry, and click on the icon button.
4) Select the icon in the directory, click "Open", then click "Save".

*Panel icon*
1) Download and extract the icon to /usr/share/pixmaps
2) If the icon is on a panel, right-click it and select properties
3) Click the icon button
4) Select the icon from the list that comes up.
5) Click "OK", and then "Close".

-------------------------

**Gnome main menu**
1) Download and extract the icon to /usr/share/pixmaps
2) Open the configuration editor (Main menu->System tools->Configuration editor)
3) Go to /apps/panel/objects and expand it (Click the little arrow)
4) You will see a series of folders with names like "object_2", "object_3", etc
5) Look through those folders and find the one with a "tooltip" value of "Main Menu" in the right side of the window
6) Check "use_custom_icon"
7) Click twice on the value column of the "custom_icon" field
8) Enter "name_of_file", without quotes, replacing name_of_file with the name of the file WITH THE EXTENSION
9) Click out of the field; the change should be immediate
10) When you're done, close the Configuration editor

---

### Post by #Vizc@ch@ on 2005-04-06
I can't install new icon themes, why could it be? I follow the exact steps but after I drag the file and agree to install ... it doesn't add it to the list  :|

---

### Post by WMCoolmon on 2005-04-07
What are some of the packages you tried to install, and did it give you any errors when you dragged them over?

---

### Post by LongTooth on 2005-04-07
I have to admit that despite being involved in Linux for some years, I've yet to master or even come near mastering anything to do with theme, style or icon installation with Gnome.  Since my efforts were puny by comparison maybe that is why. I'm not a KDE user and have never tried this with it although I've heard is much easier. I've followed the steps at gnome-look and other sites to enhance my systems without much success. While I'm not too keen on this aspect of Linux I am as attracted to eye candy as any other. I'll give this a look and what I can do with it. Thanks for the HowTo.

---

### Post by arctic on 2005-04-07
for those who have trouble with icon themes not working correctly (=not installed correctly), untar the icon theme and move the folder to your /home/username/.icons folder. if you want the icon theme to be available for everyone and forever, copy the theme as superuser to your /usr/share/icons folder.

---

### Post by #Vizc@ch@ on 2005-04-07
Thank you very much, that worked  :D

---

### Post by Perfect Storm on 2005-04-09
To change more icons manually take also a look in /usr/share/icons/hicolor/48x48/apps

---

### Post by mattack on 2005-04-19
I installed gcursor and some updates to the gimp at the same time. Now all my icons on my desktop and in nautilus are smaller than before (see attached screenshots). This is very annoying. I tried uninstalling gcursor to see if that would fix it but no...
I fixed it by reinstalling the icon theme.
Just thought I'd share in case anyone else had the same problem.

---

### Post by ]SK[ on 2005-07-07
Thanks for this.  Very useful!

---

### Post by Vetto on 2005-07-11
> **WMCoolmon]I couldn't find a unified guide on how to actually *use* skins, and had to find stuff out from scattered threads on the forums. For future reference by me (When I forget something, which I know I will) and anyone else, I put together this guide.

I've based it on my experience with the stuff from [gnome-look.org](http://www.gnome-look.org ), which has lots of very nice themes (Some Ubuntu-specific).

--------------------------------------------------

**Notes:**
- Every time you see a dollar sign inside quotation marks, it means to enter that command from the console as it appears within the quoation marks. For example:
"$ ls -l"
- I assume you have the extra repositories ([http://ubuntuguide.org/temp/#extrarepositories](http://ubuntuguide.org/temp/#extrarepositories)) set up for this guide.

**Downloading and extracting to /usr/share/pixmaps**
Several times I say to download/extract something to /usr/share/pixmaps said:**
> http://ubuntuguide.org/temp/#menu-editor[/url])
2) Download & extract the icon to /usr/share/pixmaps
3) If the app is in the menu, use the menu editor to select the entry, and click on the icon button.
4) Select the icon in the directory, click "Open", then click "Save".

*Panel icon*
1) Download and extract the icon to /usr/share/pixmaps
2) If the icon is on a panel, right-click it and select properties
3) Click the icon button
4) Select the icon from the list that comes up.
5) Click "OK", and then "Close".

-------------------------

**Gnome main menu**
1) Download and extract the icon to /usr/share/pixmaps
2) Open the configuration editor (Main menu->System tools->Configuration editor)
3) Go to /apps/panel/objects and expand it (Click the little arrow)
4) You will see a series of folders with names like "object_2", "object_3", etc
5) Look through those folders and find the one with a "tooltip" value of "Main Menu" in the right side of the window
6) Check "use_custom_icon"
7) Click twice on the value column of the "custom_icon" field
8) Enter "name_of_file", without quotes, replacing name_of_file with the name of the file WITH THE EXTENSION
9) Click out of the field; the change should be immediate
10) When you're done, close the Configuration editor
 Cant change the cursors...?  Tried gcursor to no avail.  I found in /usr/X11R6/lib/X11/icons/default/index.theme "inherits Human" ...this does not change with the theme selected and the Human theme has its own cursors.  Do I have to add the cursors to the saved custom theme manually or should this work as advertised?

---

### Post by songochain on 2005-07-12
I Cant change the cursor, I did all but cursor doesnt change. I've Ubuntu breezy
Have I restart? I did log out to see any change but nothing happens...

---

### Post by atilasendil on 2005-07-15
Respect.

This is my first post here on ubuntu forums;
and third day with ubuntu and linux (other than trying some distros 6 years ago)
ubuntu is here to stay on my computer :-)
and thanks to you people I am so happy about my ubuntu ...

Atila.

---

### Post by WMCoolmon on 2005-09-04
Could someone move this thread to the HOWTO forum (if there isn't already a similar one there)?

---

### Post by strabes on 2006-09-25
I can't seem to change the main menu icon. Bummer. I want to make it an apple like OS X. I've got all the custom OS X icons and everything, this is the last thing I need to change. Has anyone else tried this on dapper?

---

### Post by qamelian on 2006-09-25
> **strabes said:**
> I can't seem to change the main menu icon. Bummer. I want to make it an apple like OS X. I've got all the custom OS X icons and everything, this is the last thing I need to change. Has anyone else tried this on dapper?

I believe you can do this in gconf-editor. Press alt-F2 to get the "Run Application" box and type gconf-editor in the command line. When gconf appears, drill down to ```
/apps/panel/default_setup/objects/menu_bar/custom_icon
```Double-click on "custom_icon" and enter the path and filename to the icon you want to use. Close gconf. You may need to restart the panel containing the menu, but I'm not sure. I think the new icon should just appear.

---

### Post by Factory on 2007-03-09
When trying to use gcursor, it seems that only a few of the cursors are changed. The one that displays an arrow and an watch still displays as the human theme, as does the hand cursor. This goes for every theme, including the ones that come with gcursor.

---

### Post by Factory on 2007-03-09
Alright, now one of the themes froze up my gnome panel. It was killed. Where do I go from here, oh wise ubuntu gurus?

---

### Post by Perfect Storm on 2007-03-10
<alt>+<F2>

```
gnome-theme-manager
```

Then change to another theme.

> When trying to use gcursor, it seems that only a few of the cursors are changed. The one that displays an arrow and an watch still displays as the human theme, as does the hand cursor. This goes for every theme, including the ones that come with gcursor.
You need to logout and login again.

---

### Post by Factory on 2007-03-10
> **Artificial Intelligence said:**
> Words words words.

AH. Thank you!

Ubuntu's community is by far the best =)

---

### Post by allforcarrie on 2007-04-12
i love this thread.

---

