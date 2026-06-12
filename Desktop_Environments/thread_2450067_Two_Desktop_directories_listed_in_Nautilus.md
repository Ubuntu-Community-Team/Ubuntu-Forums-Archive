---
title: "Two Desktop directories listed in Nautilus"
date: 2020-09-06
forum: Desktop Environments
---

### Post by nought2 on 2020-09-06
Files and .desktop launchers are no longer visible in the GUI desktop of my Ubuntu 20.04.1 system.
This happened after a session operating as root to create lists of directories and files in EFI partition. 

EFI partition was mounted at /mnt .
Via terminal working out of ~/Desktop directory output of ls command was directed to .txt files in  ~/Desktop.

As far as I was aware I didn't go anywhere near changing anything - no settings, no editing of files, only listing directory contents and making .txt files containing command outputs. 

Afterwards files saved to ~/Desktop could be seen in Nautilus but they were not visible in GUI. 
I noticed Nautilus now has two /Desktop listings. See screenshot:
[ATTACH=CONFIG]286896[/ATTACH]

Assistance to remove surplus Nautilus /Desktop listing and restore normal GUI Desktop would be appreciated.

---

### Post by Dennis N on 2020-09-06
The section of the sidebar between USB devices and '+ Other Locations' is where bookmarks go. So is the second "Desktop" just a bookmark?

---

### Post by nought2 on 2020-09-06
> **Dennis N said:**
> The section of the sidebar between USB devices and '+ Other Locations' is where bookmarks go. So is the second "Desktop" just a bookmark?Yes, I suppose it could be used for bookmarks. However I did not intentionally create one there.

Right clicking on the extra /Desktop listing brings up a context menu including option to remove:
[ATTACH=CONFIG]286897[/ATTACH]

I didn't want to try that option in case it might exacerbate the problem.

Having just clicked the 'remove' option the /Desktop false shortcut or bookmark disappeared. Unfortunately normal GUI function was not restored.
Now have only one /Desktop listing and a hamstrung Desktop GUI.

Another symptom: The job for the .desktop launcher saved to /Desktop is to reduce number of clicks to shutdown/restart system. When the listed file is clicked it doesn't launch the shutdown function like it is supposed to, just opens file in default text viewer.

---

### Post by nought2 on 2020-09-06
I tried rebooting the system.

That initially seemed to restore Desktop GUI function.
Was able to see files saved to Nautilus /Desktop directory.

.desktop launcher was there too. While trying things to restore its function earlier I had deleted .desktop file from Desktop and copy-pasted the original saved .desktop launcher to /Desktop again.

New .desktop launcher file had generic icon with gear motifs. Right click produced context menu with open to 'permit launching' or similar.
Clicking that option restored launcher's icon and function. Terrific. All looked fixed. 

But no. To complete test I copied a few .txt files to /Desktop. After doing that the .desktop launcher file had reverted to geared motif and would not launch. I have checked that it is executable. Clicking the the launcher file from Desktop GUI opens it in text editor, does not launch shutdown function.

---

### Post by nought2 on 2020-09-07
When all else fails one can always resort to restoring a backup image.
In this instance the clock only had to be wound back 5d.

All good. Sorted.

In future I'll be taking extra special care when working as root.
I'll be extremely reluctant to use special system directories to operate from.
Won't be using /Desktop again. Will create a /test directory in /home/user instead.
Once bitten, etc.

---

