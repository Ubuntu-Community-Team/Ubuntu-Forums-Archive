---
title: "Can Dolphin be set fpr file tree view on left side panel ?"
date: 2008-07-20
forum: Desktop Environments
---

### Post by Sweet Spot on 2008-07-20
I much prefer to have my directory be sorted in file tree view on the left side (much like how Nautilus is able to) where when you click on something like "Home", the rest of the sub folders in that directory drop down and such. It's more convenient because you can have a directory in view, while being in a totally different directory and just copy from one to another without having to click on the back or forward arrows. 

Is there a way to do this with Dolphin ?

Doug

---

### Post by benerivo on 2008-07-20
Yes you can.

From the main menu, View>Panels>Folders adds a 'tree' list. Plus, View>View Mode>Columns sets the main window area in to vertical divisions, and every time you open a folder it adds a new division so /home/thomas/Videos/Old will be shown with four divisions.

---

### Post by Sweet Spot on 2008-07-20
That's weird. Why don't I have that option ?

---

### Post by benerivo on 2008-07-20
Sorry, this is one of the new features in kde4. I'm guessing you are using kde3. You could install dolphin-kde4 and use it within kde3 if you wanted.

---

### Post by Sweet Spot on 2008-07-20
Oh, I automatically assumed that when I downloaded the latest version of Kubuntu that it was KDE 4. Well, hmm. This is a dilemma now isn't it ? Do you think I'd lose any of the stability of KDE 3 if I did as you suggested ? If not, how would I go about installing just dolphin KDE 4 over KDE 3 ?  Also, is it possible to just install Nautilus, and if so would that mess anything up ?

Doug

---

### Post by benerivo on 2008-07-21
You could either do sudo apt-get install dolphin-kde4, or sudo apt-get install nautilus. They both might come with a lot of other kde4 and gnome packages respectively, that need to be installed alongside them. They will both work and should not cause any stability problems, but the functionality may be lost. For example when you double click on a desktop location (eg. a usb drive icon), then it will open with the kde3 dolphin. You can change this in the Control Centre preferences, but i can't remember exactly how. They would also both look out of place with the styling and icon set that you have in kde3 programs.

---

### Post by McNils on 2008-07-21
Why not use konqueror?

---

### Post by benerivo on 2008-07-21
> **McNils said:**
> Why not use konqueror?

A fine point (!). Much better than using nautilus or dolphin-kde4. Also, i think i know how you can change the default file manager. In the kde control centre (or the konqueror perferneces), go to File Associations and look under inode. Change all of the items which list Dolphin as the default package, so that konqueror appears above it in the list.

---

### Post by Sweet Spot on 2008-07-24
Scratch that last remark. Dolphin KDE 4 uninstalled. Using Konqueror. Tis good.

---

