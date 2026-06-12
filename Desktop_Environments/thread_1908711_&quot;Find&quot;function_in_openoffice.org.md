---
title: "&quot;Find&quot;function in openoffice.org"
date: 2012-01-13
forum: Desktop Environments
---

### Post by jimw on 2012-01-13
I'm a writer, and I use openoffice.org on Ubuntu10.04.  Unfortunately, recently something has gone wrong with the "find" function.  When asked to find all instances of a word, it finds instead various random groups of letters.

This is a serious problem for my business.  Does anyone know hat the problem is, and better yet, how to correct it?

JimW

---

### Post by claracc on 2012-01-14
what version of openoffice are you using?.

I am using openofffice 3.3.0 and find key works well.

Perhaps there is some corruption in your openoffice profile, you can try to reset your user profile as is indicated in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?t=12426](http://user.services.openoffice.org/en/forum/viewtopic.php?t=12426), go to section Resetting the user profile

---

### Post by squenson on 2012-01-14
In the "Find and Replace" window, click on the button "More Options" and make sure that the option "Similarity search" is NOT checked.

---

### Post by jimw on 2012-01-14
> **claracc said:**
> what version of openoffice are you using?.

I am using openofffice 3.3.0 and find key works well.

Perhaps there is some corruption in your openoffice profile, you can try to reset your user profile as is indicated in this link:
[http://user.services.openoffice.org/en/forum/viewtopic.php?t=12426](http://user.services.openoffice.org/en/forum/viewtopic.php?t=12426), go to section Resetting the user profile

I am using openoffice 3.2, the only one available through the ubuntu lists.

I looked at the tutorial link, but I couldn't find any such thing as Profiles.

JimW

---

### Post by IanW on 2012-01-15
> **jimw said:**
> I am using openoffice 3.2, the only one available through the ubuntu lists.

I looked at the tutorial link, but I couldn't find any such thing as Profiles.

JimW

OpenOffice was made by Sun Micro. When Sun were bought out by Oracle, most of the OpenOffice Devs left & forked OpenOffice into LibreOffice.

Ubuntu switched to LibreOffice some time ago, which in Oneiric (Ubuntu 11.10) is currently at version 3.4.4-0ubuntu1

---

### Post by claracc on 2012-01-15
> I looked at the tutorial link, but I couldn't find any such thing as Profiles.

I copy instructions to reset opeoffice profile from link provided:
***************************************************************

Resetting the user profile

Postby Hagar Delest » Sun Nov 23, 2008 1:08 am
A corruption of your profile can sometimes occur (an OS crash when using OOo for example). If you notice some strange behavior of OOo or if it just crashes or doesn't start, the first thing to try is to reset the user profile.

    * First close OOo, including the Quickstarter (OOo icon in system tray) if activated.
      NB: make sure that there is no soffice.bin process in the task manager (Ctrl+Shift+Esc under Windows). Kill them if needed.
    * Open your file browser, make sure that it shows the hidden files and folders.
          o GNU/Linux: Ctrl+H (Nautilus, Thunar, PCMan FM, ...)
          o Windows: open Windows Explorer. Click Organize>Folder and Search Options or Tools>Folder Options (depending on Windows version). Click the View Tab and check the radio button Show hidden files, folders and drive. Click OK.
    * Rename the profile: change the \user folder (see here for its location) to \user.old for example. This way, you still keep a backup of your configuration.
    * Restart OOo, it will create a new profile. You should go through the welcome process again (if not, you may have not reset the profile properly). Note that if you had a version 2.x installed before, version 3 asks if you want to transfer your personal data, that is import your former 2.x profile. Don't check that option! It can wreck the new profile because of deprecated configuration files.
    * See if the issue has been fixed or not.
          o Not fixed. Then the user profile may not be involved and you can replace the new profile by the old one (delete the new and rename back the old one to \user).
          o Fixed. It means that one or few configuration files have been damaged. But it doesn't mean that the whole profile is dead. If you've heavily customized OOo, you can still try to retrieve some parts of your configuration: as you have kept a backup, copy the subfolders (one at a time), and restart OOo to see if the issue is back or not. You can therefore spot from where the issue comes.
***************************************************************

---

### Post by claracc on 2012-01-15
Your user folder for openoffice has to be in /home/user_folder/.openoffice.org/

> I am using openoffice 3.2, the only one available through the ubuntu lists.

You can always install the most recent openoffice 3.3.0 from the oficial website following the steps in this guide [http://user.services.openoffice.org/en/forum/viewtopic.php?t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?t=68)

To use libreoffice or openoffice is a question of what works better for you.

---

### Post by Krytarik on 2012-01-15
Just to remind you all, the OP is running Lucid 10.04, in which OpenOffice.org is still the default and only office suite included in the official repos. However, one could install LibreOffice via the deb-packages offered on its website. But I believe that wouldn't really make a difference here. Have you already tried this!?:
> **squenson said:**
> In the "Find and Replace" window, click on the button "More Options" and make sure that the option "Similarity search" is NOT checked.
Regards.

---

