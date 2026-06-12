---
title: "How to Change Default Save To Location"
date: 2010-01-27
forum: Desktop Environments
---

### Post by Dweomer on 2010-01-27
When I save an image, I'd like the default to save to /Pictures, or at least my user directory instead of /Downloads. When I download a torrent I'd like it to ask me where to save it to. When I save an MP3 I'd like it to save to the Music folder.

How do I change these preferences? I'm using Karmic Koala.

---

### Post by mcduck on 2010-01-28
I assume you are talking about saving files from your web browser? In that case that's also where the setting is, in your browser's preferences.

If you are using Firefox, just go to edit/Preferences, and on the General-tab you'll find setting where the files should be saved. Sadly Firefox doesn't have any options that would alow selecting different locations for different types of files.

For the torrents, the setting will be in your torrent application's preferences.

---

### Post by Dweomer on 2010-01-28
> **mcduck said:**
> I assume you are talking about saving files from your web browser? In that case that's also where the setting is, in your browser's preferences.

If you are using Firefox, just go to edit/Preferences, and on the General-tab you'll find setting where the files should be saved. Sadly Firefox doesn't have any options that would alow selecting different locations for different types of files.

For the torrents, the setting will be in your torrent application's preferences.

So there is no way to change preferences for that on the GUI side? Like a theme change or change to Nautilus preferences? You are of course right about it being a browser setting, which I didn't realize, but it's the same little pop up no matter which program I'm using and that's what I want to change, if I can.

---

### Post by mcduck on 2010-01-28
No it can't be Nautilus preference since it's not Nautilus that's saving the files, it's whatever program you are using at the time. The dialog just looks the same since all the programs use GTK to draw the dialog.

---

### Post by Seq on 2010-01-28
> **Dweomer said:**
> So there is no way to change preferences for that on the GUI side? Like a theme change or change to Nautilus preferences? You are of course right about it being a browser setting, which I didn't realize, but it's the same little pop up no matter which program I'm using and that's what I want to change, if I can.

Most applications default to using "XDG_DOWNLOAD_DIR", which is defined in .config/user-dirs.dirs

Custom save locations could probably be hacked into Firefox since it can save actions based on file type already (Maybe an extension already exists).

You could also write a shell script, then set Firefox to open the filetypes you wish with that script. Firefox will download the file to a temp directory and pass the filename to the script. The script would parse the output of `file ${1}` or do some regex matching on the file name, and take the appropriate action you desire (move to X, move to Y, etc).

This level of mime-type preferences will likely not be a feature of Gnome itself.

---

