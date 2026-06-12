---
title: "How do you edit the &quot;Places&quot; menu in the menubar?"
date: 2009-08-06
forum: Desktop Environments
---

### Post by bloozguy on 2009-08-06
There is a thread similar to this with three pages of no answer whatsoever.

 "Edit Menus" does NOT include the "Places" menu ... why ever not?

  Since I switched to 9.04 my folder icons eg "Home Folder" brings up the Movie Player!???

  I assume this menu is hidden somewhere in /Home since this was not changed when I went to 9.04 ... where the heck is it?

---

### Post by pastalavista on 2009-08-06
The only way I know to edit the Places menu is to add Bookmarks in the top of any Nautilus file browser window. 

To change what app an icon or file opens, right-click and select 'open with'. It will remain default until you open it with a different app.

---

### Post by decoherence on 2009-08-06
> **bloozguy said:**
> There is a thread similar to this with three pages of no answer whatsoever.

 "Edit Menus" does NOT include the "Places" menu ... why ever not?

  Since I switched to 9.04 my folder icons eg "Home Folder" brings up the Movie Player!???

  I assume this menu is hidden somewhere in /Home since this was not changed when I went to 9.04 ... where the heck is it?

that menu is not entirely editable, but you might find what you need in the invisible file .gtk-bookmarks in your home folder

---

### Post by bloozguy on 2009-08-07
I see SOME of the entries from the "Places" menu in .gtk-bookmarks and yes you can edit (just those) via Nautilus Bookmark  BUT where are the rest of the entries like the "Home" folder and how do I change it so it once more uses the file browser and not the %$&$* movie player if I can't even get to choose the app involved.
  I mean a right click on the menu item just invokes it ... no "properties" to play with or "Open with" option anywhere.
Murrrrr!!

---

### Post by wojox on 2009-08-07
Try .config/user-dirs.dirs

---

### Post by bloozguy on 2009-08-07
I searched .config right down to
"grep Places */*/*" and came up empty ....

---

### Post by wojox on 2009-08-07
Open a terminal:
```
gksudo gedit .config/user-dirs.dirs
```

---

### Post by bloozguy on 2009-08-07
See, no "Places"


```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Photos/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by SunnyRabbiera on 2009-08-07
The "edit menus" application mainly works for the application and system menu, the places menu is controlled by nautilus (the file browser).
The places menu can be edited mainly by opening up your file browser, go up to bookmarks and then selecting "edit bookmarks"

---

### Post by drs305 on 2009-08-07
> **bloozguy said:**
> and how do I change it so it once more uses the file browser and not the %$&$* movie player if I can't even get to choose the app involved.
  I mean a right click on the menu item just invokes it ... no "properties" to play with or "Open with" option anywhere.
Murrrrr!!

If you are trying to change what the default or options are when you click on a folder, take a look in ~/.local/share/applications/mimeapps.list

If you want a folder to open with nautilus instead of something a bit more unusual, look at the "inode/directory=" listing.

Changing the line to the following should open folders with nautilus on a standard ubuntu install:
> inode/directory=nautilus-folder-handler.desktop

---

### Post by rainwalker on 2009-08-07
In a Nautilus window, click the button in the side panel that says whatever view you're in (Tree, Places, Information, etc) and change it to Places. Then just drag-and-drop whatever you want to show up.

---

### Post by asmoore82 on 2009-08-07
> **wojox said:**
> Open a terminal:
```
gksudo gedit .config/user-dirs.dirs
```

!! The `gksudo` part here is unnecessary and potentially harmful.
You don't need special privilege to edit your own ".config"
```
gedit ~/.config/user-dirs.dirs
```

---

### Post by bloozguy on 2009-08-08
QUOTE:  The "edit menus" application mainly works for the application and system menu, the places menu is controlled by nautilus (the file browser).
The places menu can be edited mainly by opening up your file browser, go up to bookmarks and then selecting "edit bookmarks"
__________________

No. No. No. No  Of the 11 items in the Places menu exactly 3 (three) show up in the Nautilus Bookmarks. Why should this be, in ANY way so arcane? I mean WTF?

---

### Post by nyhm on 2009-12-07
I used a combination of two suggestions in this thread to move the (annoying) Music, Pictures, etc., folders from my home dir.

a) Edit ~/.config/user-dirs.dirs (renaming the directory locations)

b) However, this breaks Nautilus's bookmarks (apparently it doesn't read the user-dirs.dirs file) and the Places menu becomes empty. If you want these Places back:

[LIST=1]
[*]Open Nautilus (the "File Browser")
[*]Bookmarks->Edit Bookmarks...
[*]Edit each bookmark's directory to match that in user-dirs.dirs
[/LIST]
Now, the Places menu shows those bookmarks again. Notice that Gnome seems to understand the changed Desktop directory automatically.

---

### Post by Sodear on 2010-05-26
> **drs305 said:**
> If you are trying to change what the default or options are when you click on a folder, take a look in ~/.local/share/applications/mimeapps.list

If you want a folder to open with nautilus instead of something a bit more unusual, look at the "inode/directory=" listing.

Changing the line to the following should open folders with nautilus on a standard ubuntu install:
I have the same problem but do not understand quite how to change the line.  I cannot edit directly in the mimeapps list and if I do gksudo gedit ---mimeapps.list I get a new window into which I can paste the old list and edit and then save it - but that did no good - it is saved somewhere but the old mimeapps list still shows up unchanged.  I've upgraded to Lucid Lynx and this happened after the upgrade.

---

### Post by drs305 on 2010-05-27
> **Sodear said:**
> I have the same problem but do not understand quite how to change the line.  I cannot edit directly in the mimeapps list and if I do gksudo gedit ---mimeapps.list I get a new window into which I can paste the old list and edit and then save it - but that did no good - it is saved somewhere but the old mimeapps list still shows up unchanged.  I've upgraded to Lucid Lynx and this happened after the upgrade.

First, the instructions I posted may or may not apply to Lucid. When looking at older posts that is always something to take into consideration.

If you open the file and it is blank, either the path/filename was incorrect or the file doesn't exist. If gedit opens a blank file, it means it couldn't find one at the location you specified and will create a new (empty) one.

The mimeapps.list file should be owned by you and should not need to be edited as root. If you do not have a mimeapps.list file in ~/.local/share/applications, it could be that you have no 'non-default' settings for opening specific files. Find the file in a file browser (make sure you can see hidden folders/files) and then right click on the file and try to open it that way with the default text editor.  

There were several different requests in this thread. If you restate exactly what you want to do and can't it would be helpful. It would probably be best to start your own thread, but if your problem is the same as one already in this post, let us know what you want to do. If you still think editing the mimeapps.list file is the solution, post the contents of yours:  /home/yourusername/.local/share/applications/mimeapps.list

---

### Post by WinRiddance on 2010-05-27
Wow, all of these answers are really confusing, at least to me.
When I opened up Nautlius after upgrading to 10.04 my view was pretty much the same as with Karmic. Top left had all of the default places, none of which include music, pictures, etc. since those are strictly file/home and volume locations. Then to the right is where all of the results can be seen when clicking on an item from the left side. Now, if I'm understanding this thread correctly, the issue from the first poster seems to be related to **the lower left portion** of the Nautilus screen ??? If that's the case, just right click on each item that you don't want to see there, followed by clicking on **Remove**, it's that simple.

You can also add additional items there via bookmarks since that's what all of those items in the lower left portion of Nautilus are in the first place. Since I keep all of my docs, pics, vids, etc. on a separate partition that's what I had to do. You can even rename your newly created bookmarks. Although there's a bug with that (already reported) there's a very simple workaround.

[COLOR=DarkRed]**Bug workaround for renaming bookmarks in Nautilus:**[/COLOR] Find the folder that you want to rename _before_ you make a bookmark out of it by locating it from the file system or home/user at the upper left. When you see the folder that you want to bookmark on the right side ... right click on it and select rename ... copy the highlighted portion of that text **and only then** type whatever you want for your bookmark name to be. Hit enter and then open up that renamed folder by clicking on it. **Now create your bookmark** and it will show up with the desired bookmark name on the lower left side of Nautilus. Since you were smart enough to copy the initial name first you can now back out of that folder and rename it back to what it used to be originally by right clicking, then rename again, and then simply pasting the previously copied name.
**Your bookmark titles will remain intact.**
.

---

### Post by Sodear on 2010-05-27
Thank you very much.
I was trying to follow the instructions posted by Arun Chandranath ([http://ubuntuforums.org/showthread.php?t=964392](http://ubuntuforums.org/showthread.php?t=964392)) since I found a line in my mimeapps.list which read "inode/directory=rhythmbox.desktop; = nautilus-folder-handler.desktop;
I wanted to delete the reference to rhythmbox but could not do so since I did not know how to edit it.  The file I created by using gksudo gedit now resides in my user folder under the name 'cat' and has a lock symbol on it.
**_[COLOR=Black]Question: I guess it is now safe to delete this file?[/COLOR]_**
Anyhow, following your advice I found the mimeapps list in ~/.local/share/applications and was able to open it and delete the reference to rhythmbox.
THIS SOLVED THE PROBLEM.
My Places list now WORKS and brings up whatever listed Place is clicked.
I hope this will help others who are having the same problem.
Sudhir

---

### Post by drs305 on 2010-05-27
> **Sodear said:**
> Thank you very much.
I wanted to delete the reference to rhythmbox but could not do so since I did not know how to edit it.  The file I created by using gksudo gedit now resides in my user folder under the name 'cat' and has a lock symbol on it.
**_[COLOR=Black]Question: I guess it is now safe to delete this file?[/COLOR]_**

Glad you resolved this issue. The file "cat" was created while you were using *root* privileges so it is owned by root even though it is in your home folder. 

The safest way for you to remove it is to open your file browser, again as root. You can delete any file on your computer so make sure you have the correct file. Also, by highlighting the file and using SHIFT-DEL, you will bypass placing it in root's trash (which is a good thing but again make sure you have the correct file).

To open your file browser as root, use the "gksu" command.
Example:
```
gksu nautilus ~/

```
You may have to change the settings to see the hidden folders (CTRL-H in nautilus).

---

