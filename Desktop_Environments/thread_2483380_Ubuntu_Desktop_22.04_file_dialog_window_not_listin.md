---
title: "Ubuntu Desktop 22.04 file dialog window not listing folders on top"
date: 2023-01-28
forum: Desktop Environments
---

### Post by darkod on 2023-01-28
Hello all,

I am not sure if this was discussed and resolved before. I did my best with various google searches and nothing came up.

After my upgrade of Ubuntu Desktop 20.04 to 22.04 I see strange behaviour in the file dialog windows.

The standard Files/Nautilus looks OK when I open it. The central part shows first folders A-Z and then the files A-Z. If I go to the Menu -> Preferences in Files, the option "sort folders first" is selected. So all looks good there.

However, opening any type of file upload/save dialog, is showing the list in the dialog as mix of files and folders. Of course, I can click on column names and order by Name or Modified, but it is still the mix of both files and folders without giving precedence folders to be on top. For example a simple upload to Google Drive is annoying because you can't quickly browse through the folder structure because the folders and not at the top in the dialog window to select which file you want to upload.

Is this an issue others have seen or just my Ubuntu is acting up??

Thanks for any help if possible to get it back to "normal".

---

### Post by deadflowr on 2023-01-28
Save dialogs are run by the  dconf/gsettings gtk file chooser schema setting so check those in dconf at org > gtk > Settings > FileChooser.
You can ether install dconf-editor if you prefer a gui, or run
```
gsettings get org.gtk.Settings.FileChooser sort-directories-first
```
if false you can change to true like so
```
gsettings set org.gtk.Settings.FileChooser sort-directories-first true
```

See if that helps

---

### Post by Dennis N on 2023-01-28
If you right-click inside the file-chooser dialog window, you should get a context menu with a checkbox "sort folders before files". See screenshot.

---

### Post by darkod on 2023-01-28
Thanks Dennis, that worked.

@deadflowr, I have no problems working in the CLI but since the suggestion from Dennis was a right-click in the dialog it looked like more appropriate to do. Maybe the CLI commands would have worked too.

PS. Actually I removed again the checkbox from Dennis' image, so again the files and folders are mixed, and I checked the CLI setting and it seems to be 'true' but doesn't work then??
```
darko@nuc11:~$ sudo gsettings get org.gtk.Settings.FileChooser sort-directories-first
[sudo] password for darko: 
true
```

Is this a bug?

The right-click menu in the dialog does help though. The CLI setting doesn't seem to.

---

### Post by monkeybrain20122 on 2023-01-28
I just use nemo as my default file manager. Nautilus is a waste of space. Sorting folders before files is a small issue (it works in Nemo) but in general it is getting stripped of all its features but with more and more restrictions it is just PITA to use.

---

### Post by deadflowr on 2023-01-28
> **darkod said:**
> Thanks Dennis, that worked.

@deadflowr, I have no problems working in the CLI but since the suggestion from Dennis was a right-click in the dialog it looked like more appropriate to do. Maybe the CLI commands would have worked too.

PS. Actually I removed again the checkbox from Dennis' image, so again the files and folders are mixed, and I checked the CLI setting and it seems to be 'true' but doesn't work then??
```
darko@nuc11:~$ sudo gsettings get org.gtk.Settings.FileChooser sort-directories-first
[sudo] password for darko: 
true
```

Is this a bug?

The right-click menu in the dialog does help though. The CLI setting doesn't seem to.

Don't sudo, not needed.
The setting is user specific.

Edit: But yes, Dennis' solution is probably the quickest and easiest, once you know it.

---

### Post by monkeybrain20122 on 2023-01-28
> **deadflowr said:**
> Don't sudo, not needed.
The setting is user specific.


@OP
Those settings can be edited from the dconf editor if you don't remember the commands, I never remember them.

```

sudo apt install dconf-editor
```

---

### Post by darkod on 2023-01-28
Ah, OK.

But it still does the same. The output says it is already 'true' but only doing the right-click and the checkbox works as expected.

---

