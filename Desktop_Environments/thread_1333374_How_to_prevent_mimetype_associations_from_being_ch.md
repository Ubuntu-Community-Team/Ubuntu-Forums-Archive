---
title: "How to prevent mimetype associations from being changed?"
date: 2009-11-21
forum: Desktop Environments
---

### Post by skullmunky on 2009-11-21
Whenever I install a new app, it registers the mimetypes it handles.  Unfortunately it always gets put at the top of the list as the preferred app.  

Example 1:

I have DragonPlayer as my default player for videos.  I install HandBrake.  Now, all video files open by default in Handbrake.  

Example 2:

I install or upgrade Wine.  Now double-clicking a Python source file tries to launch Wine instead of Kate.

Example 3:

All my MP3 files open in some ID3 editor

Example 4:

All audio files of any kind open in RealPlayer which is just silly.

I know how to change this, of course, but it's tedious because you have to do it for every single filetype.  Isn't there some way to 'pin' the preferred app for filetypes/groups and keep this from happening?

---

### Post by Zorael on 2009-11-22
Applications' supported mimetypes are defined in their .desktop files. The system-wide ones lie in **/usr/share/applications** (and its subdirectories), while you have your own local settings in **~/.local/share/applications**. Whenever you set up an application order for a mimetype, it is saved in **~/.local/share/applications/mimeapps.list**.

If you want to remove a mimetype from an app completely, such as to stop RealPlayer from opening any and all video files, modify its .desktop file and omit the mimetype(s).

If you want to make an application less prominent, and perhaps end up at the bottom (or the top) of the Open With list, you can add or modify the InitialPreference tag in such a .desktop file. Quoth [mrboojive](http://ubuntuforums.org/showpost.php?p=8330062&postcount=5);
> The "InitialPreference" property determines which app is chosen to be the default (i.e., the one with the highest InitialPreference is the default). If the .desktop file for Amarok doesn't have that property, then just add a line that says "InitialPreference=9"

I don't know if there is a way to write-protect these changes, apart from making a very extensive user-specific mimeapps.list file, or making complete copies of .desktop files and placing them in **~/.local/share/applications**. If you modify the system-wide ones, the changes will be overwritten if/when that app is updated.

edit: You may need to run '**kbuildsycoca4**' after having made any changes to make KDE refresh the mime cache.

---

### Post by poikiloid on 2012-12-19
thanks. found it in  ~/.local/share/applications. made a zip backup in case i ever go back to reg ubuntu, then deleted it. ran kbuildsycoca4. restart. all good.

---

