---
title: "Urgent help: Window Title Bar has disappeared."
date: 2009-04-04
forum: General Help
---

### Post by asinha on 2009-04-04
The window title bar has disappeared for me. Although this only affects the windows that are used for browsing files on the computer. Every other software is running fine.

Here are two screen shot to describe the problem. 

[[IMG]http://img515.imageshack.us/img515/9563/screenshot1d.th.png[/IMG]](http://img515.imageshack.us/my.php?image=screenshot1d.png)

[[IMG]http://img258.imageshack.us/img258/7226/screenshot2p.th.png[/IMG]](http://img258.imageshack.us/my.php?image=screenshot2p.png)

This is an urgent issue as I need to do a big presentation on Wednesday. Please let me know if you know the solution.

Thank you.

---

### Post by asinha on 2009-04-04
please any one know the solution to this ?

---

### Post by ad_267 on 2009-04-04
Press alt-f2 and run "gtk-window-decorator --replace"

---

### Post by WinterMadness on 2009-04-04
if that dosent work, hit alt f2 and then emerald --replace

if that works, you wanna goto yer session manager and make sure that command starts up with yer comp.

---

### Post by ad_267 on 2009-04-04
> **WinterMadness said:**
> if that dosent work, hit alt f2 and then emerald --replace

if that works, you wanna goto yer session manager and make sure that command starts up with yer comp.

Yeah depends what window decorator you're using. If you're using Emerald then you'll want the above command, if you're not or you don't know what emerald is you'll want to use the gtk-window-decorator command.

If you have the compizconfig-settings-manager package installed then check the window decoration plugin is enabled and the command is set to "gtk-window-decorator --replace" or "emerald --replace". Also check there's nothing in the decoration windows box that would prevent certain windows from getting a window border.

---

