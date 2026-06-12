---
title: "Upgrade to 17.04 and desktop not working properly (Unity)"
date: 2017-07-14
forum: Desktop Environments
---

### Post by msezell on 2017-07-14
Hi all,
I upgraded to 17.04 last week and have since not been able to use the desktop as I normally would.  First all the shortcuts, files and folds that I had loaded on the desktop are not showing up in the GUI.  When I go the the desktop through nautilus, I see the files but when I click on them they do not load on the desktop.  Also when I try to load a file from LibreOffice the icon loads in the Dash but the file does not load on the desktop.  Can anyone tell me if there is a solution to this problem?

Thanks for any help,

Toshiba Satellite P775
Processor Intel® Core™ i7-2630QM CPU @ 2.00GHz × 8
Memory 7.7 GiB
Graphics Intel® Sandybridge Mobile 
OS type 64-bit

---

### Post by Autodave on 2017-07-15
My solution (and know that this opinion is not shared by everyone here) is to always do a clean install and to only use the long-term releases. I have never had any luck upgrading. Copy everything you need to a USB stick, external HD, whatever and start over.

---

### Post by CatKiller on 2017-07-15
It's not clear from your post, but as far as I can tell, you have files on your Desktop, but Unity is set to not show files on the Desktop? And otherwise those files work normally?

Whether the files in the ~/Desktop directory are actually shown on the desktop is a toggleable configuration preference (the same as whether to display removable drives or the Trash bin on the desktop). I can't tell you exactly where that configuration option is displayed, since I don't use Unity, nor 17.04, but you should be able to find it now that you know what you're looking for. In Gnome it's set with the org.gnom.desktop.background/show-desktop-icons dconf key. There's probably a similar key for Unity if you can't find a UI option to toggle it.

---

### Post by msezell on 2017-07-20
Thanks for the responses Autodave and CatKiller. There's more to the problem than just setting Unity to show files, folders and icons on the desktop.  I'm not able to get anything to load that using the desktop to launch even when I do it through Nautilus. I think I'll take Autodave's suggestion and do a clean install which is what I normally have done in the past.  Thought I'm save sometime by doing an upgrade but not the case.  Thanks to all.

---

