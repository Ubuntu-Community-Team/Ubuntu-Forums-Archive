---
title: "Gnome Menu's"
date: 2005-01-26
forum: Desktop Environments
---

### Post by oracledarren on 2005-01-26
Hi

could anybody please tell me how I can add entries into the gnome menu panel.

I have installed a few extra dev packages that it would be useful if they were in there   ;) 

Take care

Darren

---

### Post by Sham on 2005-01-26
If you mean to make a quick launch button, I tend to right click on the desktop and make laucher (pick an icon, command line etc), and then just drag it onto the panel.

Is this what you mean?

---

### Post by oracledarren on 2005-01-26
Not exactly, I want to add entries into the application menu and not on the panel.

My panel is already pretty full so I want to organise things a little better :)

Thanks

---

### Post by fng on 2005-01-26
Adding things directly beneath the Applications panel isnt possible gui-wise.
You can always add menu-items in the submenus.

Right Click on any item in the submenu - > entire menu -> add new item to this menu.

---

### Post by oracledarren on 2005-01-26
[QUOTE=fng]Adding things directly beneath the Applications panel isnt possible gui-wise.
You can always add menu-items in the submenus.

Right Click on any item in the submenu - > entire menu -> add new item to this menu.[/QUOTE]
 That exactly what I was after.

Thanks alot :)

---

### Post by ilari on 2005-01-27
Actually you can add things also directly beneath the Applications-menu. Just open 'Applications' --> 'Run Application', and type 'applications://' (without quotation marks) and press enter . This opens nautilus file-manager, and there you can right-click and choose 'Create Application Launcher'

---

### Post by oracledarren on 2005-01-27
This is perfect - I ideally wanted to make my own application groups directly off the main menu and this is it :)

Thanks alot for your help

Darren

---

### Post by bVork on 2005-01-31
I've been unable to add items to the application menu.

[QUOTE=fng]Adding things directly beneath the Applications panel isnt possible gui-wise.
You can always add menu-items in the submenus.

Right Click on any item in the submenu - > entire menu -> add new item to this menu.[/QUOTE]

I don't have this option in the submenu. The only two options I see are "add this drawer to panel" and "add this as menu to panel."

How can I enable this option?

The other method mentioned doesn't work for me either...

[QUOTE=ilari]Actually you can add things also directly beneath the Applications-menu. Just open 'Applications' --> 'Run Application', and type 'applications://' (without quotation marks) and press enter . This opens nautilus file-manager, and there you can right-click and choose 'Create Application Launcher'[/QUOTE]

I get the following message when I enter 'applications://' in Applications -> Run Application...:

"Cannot display location 'applications://'
Details: There is no default action associated with this location."

How do I fix this?

---

### Post by Tichondrius on 2005-01-31
1 - try to right click on an entry in a submenu of the applications menu (for example, right click on Firefox in the Internet submenu), then choose "entire menu"->"add launcher".

2 -  In nautilus, I believe the "path" to enter in the box showing the current directory  is "Applications:///"

---

### Post by carlc on 2005-01-31
You can adapt this excert from the [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/index.html#nvu) 
to fit what you want to do

From the terminal:

$ nautilus applications:///Office


# File Browser: Office
File Menu -> Create Launcher
Basic Tab ->
Name: Nvu
Command: /opt/nvu-0.70/nvu
Icon: /opt/nvu-0.70/icons/mozicon50.xpm

---

### Post by bVork on 2005-01-31
[QUOTE=carlc]
From the terminal:

$ nautilus applications:///Office[/QUOTE]

I get a similar error as the one in my previous post:

"applications:///Office is not a valid location.
Please check the spelling and try again."

I also tried it without the Office suffix, to no avail.

[QUOTE=carlc]
# File Browser: Office
File Menu -> Create Launcher
Basic Tab ->
Name: Nvu
Command: /opt/nvu-0.70/nvu
Icon: /opt/nvu-0.70/icons/mozicon50.xpm[/QUOTE]

I don't understand these instructions. Could you elaborate?

[QUOTE=Tichondrius]1 - try to right click on an entry in a submenu of the applications menu (for example, right click on Firefox in the Internet submenu), then choose "entire menu"->"add launcher".[/QUOTE]

As I mentioned before, I simply do not have that menu item

[QUOTE=Tichondrius]2 -  In nautilus, I believe the "path" to enter in the box showing the current directory  is "Applications:///"[/QUOTE]

I get a nearly identical error as the one earlier in this post:

"applications:/// is not a valid location.
Please check the spelling and try again."

Hm, just looking at those errors... Nautilus seems to automatically converting my "Applications:///" entry into "applications:///". Could this be the problem? And how would I force Nautilus to recognize the exact case I enter?

---

### Post by carlc on 2005-01-31
Click applications and decide where you want the shortcut to go (e.g. games, internet, multimedia, etc). It has to be a menu item that already exists. 

From the terminal type:

nautilus applications:///Office

Replace "Office" with where you want your shortcut to go.
So if you want it to go under games then type

nautilus applications:///Games

this will launch a window in which you can create  your shortcut

Click - File Menu
Click - Create Launcher


From there enter the appripriate values

Under the "Basic Tab", 
Here is an example, replace with what you are creating


Name: Nvu
Command: /opt/nvu-0.70/nvu
Icon: /opt/nvu-0.70/icons/mozicon50.xpm

---

### Post by WW on 2005-01-31
Also take a look at: [http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#applicationsmenu](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#applicationsmenu)

---

### Post by bVork on 2005-02-01
[QUOTE=carlc]Click applications and decide where you want the shortcut to go (e.g. games, internet, multimedia, etc). It has to be a menu item that already exists. 

From the terminal type:

nautilus applications:///Office

Replace "Office" with where you want your shortcut to go.
So if you want it to go under games then type

nautilus applications:///Games

this will launch a window in which you can create  your shortcut
[/QUOTE]

This does not work! I still get the error:

"applications:///Office is not a valid location.
Please check the spelling and try again."

---

### Post by carlc on 2005-02-01
Hmm, How about typing it again and then copy the text from the terminal beginng with the command you typed all the way through the error message and posting it.

---

### Post by bVork on 2005-02-01
A screenshot is worth a thousand words. Especially since the error message doesn't pop up in the terminal. See my attachment.

---

### Post by philip41 on 2005-02-01
All of the above do not work for me either, i am getting the exact same error message.Maybe something has been altered in some way with one of the recent updates.

---

### Post by dhonn on 2005-02-01
Are you doing all this under the root user?

Just making sure you guys aren't running under root.

---

### Post by Tichondrius on 2005-02-01
[QUOTE=dhonn]Are you doing all this under the root user?

Just making sure you guys aren't running under root.[/QUOTE]

this works in woody  from the command line (as normal user):

$ nautilus applications:///

and also 

$ nautilus applications:///Office

---

### Post by carlc on 2005-02-01
It looks like you are leaving a "/" out

You have:

> nautilus applications://Office

and it should be:

> nautilus applications:///Office

---

### Post by bVork on 2005-02-01
I tried varying the number of slashes, from 1 to 4. Same error every time, only with a different amount of slashes appearing in the error message.

For the record, I'm running on an almost-fresh install of Ubuntu 5.04 (Hoary Hedgehog). The only things I have changed are the desktop background, the organization of the panel, and the theme.

---

### Post by Tichondrius on 2005-02-01
[QUOTE=bVork]I tried varying the number of slashes, from 1 to 4. Same error every time, only with a different amount of slashes appearing in the error message.

For the record, I'm running on an almost-fresh install of Ubuntu 5.04 (Hoary Hedgehog). The only things I have changed are the desktop background, the organization of the panel, and the theme.[/QUOTE]

For the record, this doesn't work in hoary (e.g. gnome 2.9)

---

### Post by carlc on 2005-02-01
Tichondrius, Thanks. I did not know that. Is there a similar command?

---

### Post by bVork on 2005-02-02
Armed with the information that this is a quirk of Gnome 2.9, I went googling for some more information. Unfortunately, the most relevant items seem to be people in the same boat as me: unable to edit the menu.

[http://ubuntuforums.org/archive/index.php/t-7822.html](http://ubuntuforums.org/archive/index.php/t-7822.html)
[http://www.ubuntuforums.org/showthread.php?t=12360](http://www.ubuntuforums.org/showthread.php?t=12360)

Searching through my filesystem, I've found various files that seem to be from an older menu structure (one that has a "Debian" entry, unlike the current one.), but none that resemble the current menu.

Can anyone shed more light on this?

---

### Post by Wim Sturkenboom on 2005-02-02
Below is a template that can be used to add an application to an existing category (e.g office, accessories etc). The bold items are to be changed. Others can stay the same (as far as I know). Please note that the description below will add entries for ALL users.```
[Desktop Entry]
Encoding=UTF-8
**Name**=WimS' Editor
**Comment**=Edit text files
**Categories**=Application;Office;Utility;
**Exec**=gedit %U
**Terminal**=false
**Icon**=gedit-icon.png
Type=Application
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
StartupNotify=true
MimeType=text/plain;text/x-readme;application/x-shellscript;
```Save this file under a decent name with the extension desktop in */usr/share/applications*. I called it *wim.desktop*.

**Name** shows in the menu
**Comment** is displayed when the mouse moves over the item
**Categories** defines in which categories (this is, under applications) it will show. Here it will show in Utility (which is the accessories) and in Office (which is the office. *Applcation* is required. I will describe later how to find the categories. Don't forget the semi-colon after the last category.
**Exec** is the program to be executed. Just change the program name. The function of *%U* is unknown (I have the list ate home); I suggest you leave it in.
**Terminal** indicates if the application should run in a terminal (false for apps with a GUI
**Icon** is the icon that is shown in the menu

To find the possible categories, open the file */etc/gnome-vfs-2.0/vfolders/applications-all-users.vfolder-info* with an editor. Search for the second entry *<Folder>*. In a default installation, this is probably *Accessories*. A folder-section describes most info for an menu-folder; it's embedded between <Folder> and </Folder>. Below an example of the office entry```
    <!-- Office -->
    **<Folder>**
      <Name>Office</Name>
      <Desktop>Office.directory</Desktop>
      <Query>
	<And>
	  <Keyword>Application</Keyword>
	  <Or>
	    <Keyword>Office</Keyword>
	    <Keyword>Spreadsheet</Keyword>
	    <Keyword>WordProcessor</Keyword>
	    <Keyword>Calendar</Keyword>
	    <Keyword>ProjectManagement</Keyword>
	  </Or>
	</And>
      </Query>
      <DontShowIfEmpty/>
    **</Folder>**
```The keywords describe the categories. In this example, any desktop-file (see the first code block] containing the category application in combination with either office, spreadsheet, wordprocessor, calendar or projectmanagement will show under the Office entry in the menu.
If you look in the <Folder> section for accessories, you will find that the keyword is utility which was used in wim.desktop in the first code-block.

If you want to add a new menu in the applications menu (e.g. myprograms), simply copy an existing folder-section and modify it. Make sure that you copy it at the right place. Probably best is to add it at the end of the file just before```
  </Folder>
</VFolderInfo>
``````
    <!-- myprograms -->
    **<Folder>**
      <Name>Myprograms</Name>
      <Desktop>Myprograms.directory</Desktop>
      <Query>
	<And>
	  <Keyword>Application</Keyword>
	  <Keyword>Myprograms</Keyword>
	</And>
      </Query>
      <DontShowIfEmpty/>
    **</Folder>**
```
The **Name** is the name as it shows in the menu.
The **Desktop** refers to a directoy file in */usr/share/gnome/vfolders*
**Keyword** are explained before; you can define your own ones.
**DontShowIfEmpty/** can be removed if you want to see the menu entry although there are no applications with the correct categorie

One thing remains and that's the icon. If the file *Myprograms.directory* does not exist, you will get a simple-folder icon. Create the file /usr/share/gnome/vfolders/Myprograms.directory with the following content```
[Desktop Entry]
**Name=**Myprograms
**Comment**=My comment
Type=Directory
**Icon**=advanced-directory
```You can modify the bold items to suite your requirements. Please note that the name should be the same as in the file new folder-sections in */etc/gnome-vfs-2.0/vfolders/applications-all-users.vfolder-info*. I have not figured out yet what the exact relation is.

And that's about all I know about it. To create user specific menus, a similar approach can be used. See [http://home.comcast.net/~3rdshift/articles/linux_tips.html#menus](http://home.comcast.net/~3rdshift/articles/linux_tips.html#menus)

Note: the only file that gets modified is */etc/gnome-vfs-2.0/vfolders/applications-all-users.vfolder-info*. Make a backup before you screw around in it. All other files are created.
Note: Have a look in the different files in */usr/share/applications* and in */usr/share/gnome/vfolders* and use them as examples. I have basically copied a desktop file and a directory file for the examples above and threw out all the stuff that I did not need.

Important: you use these instructions on your own risk (although the risk is minimal).

---

