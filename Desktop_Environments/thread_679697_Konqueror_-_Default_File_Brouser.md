---
title: "Konqueror - Default File Brouser"
date: 2008-01-27
forum: Desktop Environments
---

### Post by boyan_zlatkov on 2008-01-27
Hello,
How can i make konqueror to be my default file browser in Kubuntu 7.10?
When Konqueror starts - Web Browsing profile is loaded by default and i have to click Settins - Load View Proile - File management. I want to make "File Management" Profile to be loaded automaticaly when Konqueror starts.
Thanks!

---

### Post by sumguy231 on 2008-01-27
First of all, install kcontrol because I don't know how to do this from System Settings. Then, open kcontrol and go to KDE Components, then File Associations. Under inode, select "directory" and use the controls on the right to give Konqueror highest preference. Then repeat with "system_directory".

---

### Post by bailout on 2008-01-27
I think you can get to the same thing through options in Konqueror itself.

To make konq load the file management profile just right click on the short cut icon, select properties and then look for the field that says 'webbrowsing' and change it to 'filemanagment' or maybe 'filemanager'. I can't remember which and am on windows at the moment.

---

### Post by sumguy231 on 2008-01-27
> **bailout said:**
> I think you can get to the same thing through options in Konqueror itself.

To make konq load the file management profile just right click on the short cut icon, select properties and then look for the field that says 'webbrowsing' and change it to 'filemanagment' or maybe 'filemanager'. I can't remember which and am on windows at the moment.

You should do that as well but if I remember correctly unless you change the directory file association, filesystem shortcuts and icons will still open in Dolphin.

---

### Post by fish2ways on 2008-01-27
> **boyan_zlatkov said:**
> Hello,
How can i make konqueror to be my default file browser in Kubuntu 7.10?
When Konqueror starts - Web Browsing profile is loaded by default and i have to click Settins - Load View Proile - File management. I want to make "File Management" Profile to be loaded automaticaly when Konqueror starts.
Thanks!

Kcontrol is installed by default in Kubuntu. It's just 'hidden'.

I think you're asking two questions here. To make Konqueror the default file manager instead of Dolpin click on the K menu then 'Run Command'. type in kcontrol, press enter.  Select KDE Components then File Associations. Click on 'inode' to expand the tree then select 'directory' At the right you'll see a window with Dolphin, Konqueror and Cerrvisia listed. Click on Konqueror then click on the 'Move Up' button so that Konqueror is at the top of the list. Click on 'Apply' and you're done. All folders, files etc will now open in Konqueror by default.

You're getting the Web Browsing profile opening if you click on the konqueror web browser button on the Main Panel. To get the File Management profile just click on any directory, your home folder etc and there it is. Just place a link to your home folder in the Main Panel and click on that to get File Management view.

Hope this helps

---

### Post by boyan_zlatkov on 2008-01-28
Thanks to all fo you:)!
Now it works perfectly - i've made changes to konqueror start button and to KDE Components in KControl. Thanks!

---

