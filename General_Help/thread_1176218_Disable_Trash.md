---
title: "Disable Trash?"
date: 2009-06-02
forum: General Help
---

### Post by yonyz on 2009-06-02
Hi,

Is there a way to disable the Trash on Ubuntu 9.04, so that everything will be permanently deleted?

---

### Post by talava on 2009-06-02
It should be possible via gconf-editor, if shift+delete isn't enough :)


Type 'gconf-editor' in terminal.

Go to: apps -> nautilus -> preferences and tick enable_delete.

> If set to true, then Nautilus will have a feature allowing you to delete a file immediately and in-place, instead of moving it to the trash. This feature can be dangerous, so use caution.

---

### Post by yonyz on 2009-06-02
It's already checked. I can remove the Trash icon, but I want to be able to permanently delete by only pressing Delete, that is, without Shift.

---

### Post by bruno9779 on 2009-06-02
Re map it on Admin > sys > shortcuts

---

### Post by yonyz on 2009-06-02
Already tried but couldn't find it.

---

### Post by gewone on 2010-11-24
Any news on this issue? Would be awesome. I flagged the *'enable_delete'* boolean in gconf-editor, and yet the option is added to right click, a simple press on Delete will move the stupid philes -> Recycle bin just as always. This is a non-desired behaviour. Any ideas? Please? Much appreciated. Ty in adv. Regards~

---

### Post by WorMzy on 2010-11-24
```
chmod -R a-w ~/.local/share/Trash
```

That will remove the write permissions from your Trash directory. If you cannot write there, then you cannot use the recycle bin, and will be asked whether you want the file(s) you've selected for deletion to be permanently deleted instead.

---

### Post by gewone on 2010-11-24
As it turned out, a simple *'chmod 000 ~/.local/share/Trash'* did the trick. Excellent! Hope this will help others!
Now Nautilus behaves just like Windoze, i.e. one confirm box (when pressing DEL key), then after simply pressing ENTER the file is wiped.

---

### Post by qamelian on 2010-11-24
> **gewone said:**
> As it turned out, a simple *'chmod 000 ~/.local/share/Trash'* did the trick. Excellent! Hope this will help others!
Now Nautilus behaves just like Windoze, i.e. one confirm box (when pressing DEL key), then after simply pressing ENTER the file is wiped.
No, Nautilus was behaving like Windows before. The default behaviour on every version of Windows since 95 is Delete key sends to the Recycle Bin and Shift-Delete deletes and bypasses the Recycle Bin. By default, Shift-Delete does the same thing in Gnome, as well.

---

### Post by JOHNNYG713 on 2010-11-24
Open your home folder,click edit,preferences,behavior tab and tick " include delete command that bypasses trash ".

---

### Post by gewone on 2010-11-24
> **qamelian said:**
> No, Nautilus was behaving like Windows before. The default behaviour on every version of Windows since 95 is Delete key sends to the Recycle Bin and Shift-Delete deletes and bypasses the Recycle Bin. By default, Shift-Delete does the same thing in Gnome, as well.

Sorry. I know. Thing is, ever since like W9x first thing I did after fresh install has been to right-click Recycle bin, tic "Disable Recycle Bin for all drivers" and then use eg. TweakUI or direct Registry setting to get rid of the darn icon (recent versions has made it even more easy, like a tic box for that also). Anyway, sorry. I _do know_ that the very default behaviour of Windows is to move everything to Recycle bin, it's just that I haven't seen that behaviour in so many years due to my way of always disabling it first thing.

Anyway, glad we kept this up. The *~/.local/share/Trash* thing was neat. However, it does only work with root file system. When I insert eg. memory card or suchlike, it will create that stupid *.Trash-999* folder and keep on knocking it's door. Will I be stuck here? Only solution is to actually do the *'chmod 000 ...'* procedure for each and every drive? Or is there any other smooth way?

Oh, I've also seen the way JOHNNYG713 describes the supplementary 'Delete' item on the right-click menu, which I presume is just about the same thing as happens by setting 'enable_delete' boolean to 1 in gconf-editor. Anyway, that's not my desired behaviour. I'm so used to hitting the DEL button, so no way I'm getting used to fiddling with the mouse utility, right-clicking and stuff.

So, simply said, any chance of getting *'chmod 000 */Trash'*-isch? :D


Ty in adv~
Regards~

---

### Post by gewone on 2010-11-28
Anyone?

---

### Post by ColdnitroX on 2010-11-28
What you should do is u should right click on the toolbar and put the Trash applet on it. Then left click on it. Plug all those devices with those stupid trash.999 folders on them in, then go back to that trashcan window you opened and click the button that says " Delete All " Or "Empty Trash". Wait a minute or 2 for it to finish deleting and then open Nautilus and click the Eject button beside the devices in the bar, then remove the devices from the USB ports. It should work, and restore the space on those drives in the meantime. [SIZE=5]Good Luck!:D:D[/SIZE]

---

### Post by ColdnitroX on 2010-11-28
Its a temporary fix (maybe).

---

### Post by gewone on 2010-11-30
It's a poor fix, works till next time you connect your (eg.) SD card :/

---

### Post by Zvlwab on 2011-07-26
Googled it and found a solution:

Run gconf-editor and check /desktop/gnome/interface/can_change_accels and apps/nautilus/preferences/enable_delete

launch nautilus
select a random file
click "Edit"
hover over "Delete"
press the delete button on your keyboard twice

I recommend unchecking /desktop/gnome/interface/can_change_accels in gconf-editor

That fixed it for me :)

---

