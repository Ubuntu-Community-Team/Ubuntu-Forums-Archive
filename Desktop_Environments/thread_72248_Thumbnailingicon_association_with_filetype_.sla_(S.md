---
title: "Thumbnailing/icon association with filetype .sla (Scribus)"
date: 2005-10-05
forum: Desktop Environments
---

### Post by irifan on 2005-10-05
Hi,
I am using a lot of Scribus (.sla) files.  How can I thumbnail all .sla files, or associate an icon with them?. 
Also, is there a way to open .sla files directly by double clicking? Right now, Ubuntu recongnises the file as "executable textfile" and I have to press "Display" to start Scribus.

TIA!

---

### Post by slashird on 2008-03-16
I was just trying to figure out how to do the same thing.  Found the solution that worked for me here:
[http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html).

I am running kubuntu 7.10.

   1.  Navigate to "Konqueror File Associations" (run command: kcontrol)
   2. Select your file type from the "Known Types" menu at left, or press button right below it, to enter a new file type,
   3. Select __ tab at right pane,

      [Konqueror file mime-type associations setup]
   4. Optional: Add or remove file types associated with this mime type in "Filename Patterns" menu, at the upper side of the "General" tab,
   5. Optional: Select the description and icon to be shown in Konqueror file manager for this mime type,
   6. At "Application Preference Order", define which programs will be tried in which order, to open this file type. (you'd be presented with the K-Menu applications tree to select an app from) , , and programs in the list as necessary. These programs will also show up in the "Open With" item on right-click pop-up menus, along with the "Other..." item.
   7. You can also "Edit" the applications' properties here, such as its K-Menu properties (Description, Command to run, Run as different user, Run in terminal, Place to sys-tray, etc.), or their reverse mime-type properties (i.e. which mime-types a given app supports, as opposed to the normal way of specifying which apps support a given mime-type, as we've just been doing above). These are just alternative/reverse routes to doing the same things with usual means, i.e. the K-Menu Editor (kmenuedit) and here, the mime-type editor (kcmshell filetypes).
   8. Select __ tab to choose by which means this file type should be opened: In a separate application you've just specified in the "General" tab, or in an embedded Konqueror plug-in you will soon specify below. You can specify a particular behavior (external app vs. plug-in) for this specific file type, or you can choose to inherit the behavior of the parent group. Additionally you can specify whether the content will be (dis)played right away upon clicking, or you will be asked what to do with the clicked file: Whether (dis)play as you've specified here, or save to disk, or open with another program.

      [Konqueror file/mime-type embedded viewer associations setup]
   9. In the "Services Preference Order" section at lower part of the "Embedding" tab, select which embedded plugins should be tried in which order, when this file type is to be (dis)played as plug-in. Again Add, Remove, Move Up/Down the plug-ins in the list, as necessary. There are 36 different plug-ins provided in a default Kubuntu 5.04 installation, sufficient for most embedded viewing needs
  10. Press to save all the selections you have done.

---

