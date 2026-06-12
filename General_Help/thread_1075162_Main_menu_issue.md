---
title: "Main menu issue"
date: 2009-02-20
forum: General Help
---

### Post by ForgivenByJC on 2009-02-20
Serious problem.  After the last round of updates, around this weekend sometime, the "Applications" menu of the main menu does not display.  Also I ran out of disk space around this time frame as MythTV had duplicated all of my mp3's from one hard drive to the root file system--I have since deleted them.  I have NO idea how to start with this problem.

I have added the main menu applet to another panel and the same issue.  I have reinstalled (via Synaptic Package Manager) gnome-panel, gnome-desktop, and everything related to "main menu"--no change in the issue.  When clicked, there is a little tiny square (~1mm x 1mm) but no options.  Also, selecting System -> Preferences -> Main Menu will not open the main menu dialog.  Thoughts???  For the record, the "Places" and "System" menus are still working, just "Applications" is not working.  Thanks!

---

### Post by CKDewey on 2009-02-20
You might try following the advice in this post:

[http://ubuntuforums.org/showthread.php?p=5158084](http://ubuntuforums.org/showthread.php?p=5158084)

---

### Post by ForgivenByJC on 2009-02-20
No luck.  Thank you for the advice, Tom.  I tried deleting the one file which responded to
```
grep 'Hidden' ~/.local/share/applications/*.desktop
```
Then I backed up the ~/.local/share/applications directory and deleted it, still no luck after reboot.  Other thoughts????

---

### Post by CKDewey on 2009-02-22
Maybe create another user account then 'sudo cp' the relevant files over to your current user directory? You'll probably also need to 'sudo chown' them to make them belong to your first account.

---

### Post by mc4man on 2009-02-22
go to 
~/.config/menus
and delete the file 'applications.menu' and the applications menu will return.

---

### Post by ForgivenByJC on 2009-02-23
mc4man got it!  Thanks!  What causes this problem?  Is there anything I need to do to prevent it in the future?

---

### Post by mc4man on 2009-02-23
> What causes this problem? Is there anything I need to do to prevent it in the future?
That's a 'touchy' menu, if it gets corrupted or if somehow receives an incorrectly written entry, than the applications menu becomes nonfunctional.

Why this happens probably varies, but it's no problem restoring as you've seen. When you delete it, as soon as you click on 'Applications' it gets rewritten based on a backup stored in the system.

---

