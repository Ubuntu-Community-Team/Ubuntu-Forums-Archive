---
title: "How-To EASILY fix the Xubuntu Menu-Editor"
date: 2009-02-24
forum: General Help
---

### Post by Nano_ext3 on 2009-02-24
Before I paste in my instructions, I hope that anyone who see's them can "Digg", or link to this thread wherever they can, and also give me credit , by MikeyD or Nano_ext3 from the Ubuntu Forums. That is all that I ask.

Here you go!:

---------------------------------------------------------------------------
Things to know:
---------------------------------------------------------------------------
Your XFCE menu that the "Menu Editor" app loads is located in:
"/home/USER/.config/xfce4/desktop"

What we want to do is find the menu that holds the "proper information" that holds all your current menu configurations. Open up terminal and change dir to:
"/home/USER/.cache/xfce4/desktop"

The above dir is where your current menu xml is being held, or really, is always held to the best of my knowledge. Now, do a ls, and note the files, im my case they are the following:

menu-cache--etc-xdg-xfce4-desktop-menu.xml.rc
menu-cache--etc-xdg-xfce4-desktop-menu.xml.xml
menu-cache--home-mikeyd-.config-xfce4-desktop-menu.xml.rc
menu-cache--home-mikeyd-.config-xfce4-desktop-menu.xml.xml

What holds the TRUE menu settings is the "xml" file associated with "menu-cache--etc."
To TEST this (VERY Important!) that this is the right file. Go to Applications , Settings, Menu Editor and click File -> Open. Now navigate to

"/home/USER/.cache/xfce4/desktop"

Load the proper xml associated with "menu-cache--etc." In MY* case this is :

menu-cache--etc-xdg-xfce4-desktop-menu.xml.xml

IF it loads the proper FULL menu, with ALL apps now do the steps below, if not try the other xml file associated with "menu-cache--home," but that should not be the case.
---------------------------------------------------------------------------
Steps:
---------------------------------------------------------------------------
1. Copy (in terminal using nano OR by , sudo su, then gedit the file) the contents of the "menu-cache--etc-xdg-xfce4-desktop-menu.xml.xml" file to a temporary folder AND/OR file called "XML-FIXED"

2. Open the contents of that new file. Keep it handy.

3. CD to "/home/USER/.config/xfce4/desktop

4. We are going to edit "menu.xml" Backup this file!!! First by doing copying it in file manager, or doing a "cp menu.xml menu.xml.old"

5. Open the contents of file: menu.xml with "gedit" or "nano" by doing a "sudo su" first then "nano menu.xml OR gedit menu.xml"

6. Delete ALL of the contents in "menu.xml" and replace them with the contents of "XML-FIXED".

7. Now, open Applications , Settings , Settings Manager, and click "Menu Editor". The proper menu should now be auto-loaded!!!

ENJOY!!!!

Mikey D

---

### Post by walterp98@gmail.com on 2009-05-23
I might be missing something, but I have no desktop subdirectory under xfrun4, though  I installed xubuntu 9.04.

Even when I installed [plain] ubuntu 9.04 and added xfce, I never found a menu.xml file.  Did I somehow miss something during installation?

---

### Post by Brandon Williams on 2009-05-23
The version of xfce in 9.04 (I think it's 4.6) no longer uses the menu.xml file. Instead, it is moving in the direction of the freedesktop.org menu standard used by gnome. There is currently no existing menu editor that I am aware of to edit this menu. Instead, if you're running 9.04, you might be interested in [my instructions](http://ubuntuforums.org/showthread.php?p=7240572#post7240572) for how to edit it manually.

---

