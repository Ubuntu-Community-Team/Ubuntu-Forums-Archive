---
title: "How to create shortcuts to files and folders in 18.04?"
date: 2018-05-13
forum: Desktop Environments
---

### Post by tapasray on 2018-05-13
Right-clicking on a file or folder icon does not offer creating a shortcut as one of the options in my 18.04 installation, a Windows-like feature that used to be available in earlier versions of Ubuntu. Is there some other way of creating shortcuts in 18.04? 

Thanks in advance for your help.

---

### Post by kerry_s on 2018-05-13
you mean your "copy to" is missing?

---

### Post by cruzer001 on 2018-05-13
You mean this?

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-18-04-bionic-beaver-linux)

I just use Nemo file manager.  It has the "create shortcut" option in the toolbar.

```
sudo apt install nemo
```

---

### Post by tapasray on 2018-05-13
Thanks, @cruzer001. The following answer was posted by @tomecorphic in response to my question with a different heading, i.e., a duplicate thread:

"You can press Ctrl + Shift + drag/drop the icon or you can enable the command in the context menu from Preferences / Behaviour."

It worked. 

Thanks again!

---

### Post by tapasray on 2018-05-13
No, @kerry_s. 'Create Link' was missing. Got it now. Please see above.

---

### Post by vanadium on 2018-05-15
In Nautilus Preferences, "Behavior" tab, check "Show action to create symbolic links" to restore the right-click "Create Link" menu option.

---

### Post by FoolInTheRain on 2019-02-16
> **tapasray said:**
> Thanks, @cruzer001. The following answer was posted by @tomecorphic in response to my question with a different heading, i.e., a duplicate thread:
"You can press Ctrl + Shift + drag/drop the icon or you can enable the command in the context menu from Preferences / Behaviour."
It worked. 
Thanks again!

Pressing and holding Shift+Ctrl does not work for me in 18.04 LTS

Nothing happens when I drag the file to the new folder.

Can not figure out what you mean by "Preferences / Behaviour".   Nothing like that in 18.04 LTS

---

### Post by allaptr2 on 2019-04-25
In the upper right of the Ubuntu file browser (in the menu bar), click the button with three horizontal lines. Hover over the buttons in the pop-up menu. One of the tool-tips says 'bookmark this location', click.

---

