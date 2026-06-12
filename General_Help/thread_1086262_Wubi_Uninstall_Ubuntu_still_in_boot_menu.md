---
title: "Wubi Uninstall Ubuntu still in boot menu"
date: 2009-03-03
forum: General Help
---

### Post by crapple on 2009-03-03
Hi,
I uninstalled wubi because I wanted the 32bit of Ubuntu.  To do this I removed it like a slandered windows app. But it is still in windows vista's boot menu.  How do I get rid of the Ubuntu option which dose not do anything.

---

### Post by abyrne on 2009-03-03
Hi,

  This requires downloading a Windows app called EasyBCD. Google it. Use it to remove Ubuntu from the boot menu. Then go to Control Panel\System and Maintenance\System (in Vista, don't know about XP)scroll down, click Change Settings, click on the advanced tab, click the settings button for Startup and Recovery, and uncheck the box that says Display List of Operating Systems. That should do it.

---

### Post by crapple on 2009-03-05
Thank you.  This worked great.

---

### Post by puner on 2009-04-26
Hello

Im having the same problem. But I dont have ubuntu in EasyBCD and Im also on Windows Xp.

---

### Post by wubiboy on 2009-10-06
Puner;

First Steps:

1. Boot into XP when you have the choice
2. Once your machine is started, explore the C drive.
3. Go To Tools at the top of that window and select "Folder Options"
4. Click on the "View" tab
5. Click on "Show hidden files and folders radio button"
6. Un-check "Hide Extensions for known file types"
7. Un-check "Hide protected operating system files".  You will get prompted if you are sure. Say Yes.

Now Apply those changes and you will see the target file we need to edit.

Second Steps:

1. Find the boot.ini file.  
2. Right click on that file and go to "Properties"
3. You will see that it is "read Only" checked.  Take that check mark out and click 
    apply and then OK.
4.  Right click on that file and copy it to your clip board
5.  Right click again and choose "Rename"
6.  Rename that file to boot_old.ini 
7.  Right click in any white space and select paste.
8.  You will see a copy of the boot.ini file there.
9.  Right click on that and make sure in properties it is not read only
10. Open that boot.ini file in notepad
11. In that boot.ini file is a line like  C:\ ubuntu, or very similar.  Should be last on the list possibly.
12. Delete the ubuntu line.
13. Close the file.  It will ask you if you want to save it.  Say YES
14. Right click on the boot.ini file and go to properties.  Change it back to "Read Only"

Exit back to windows and restart your machine as normal.

You will not be prompted to choose the OS again.

Make sure that you have followed these steps to the letter and in the exact order.

Good luck.

Lee

---

