---
title: "&quot;Places --&gt; Desktop&quot; is suddenly identical to &quot;Places --&gt; Home Folder&quot;"
date: 2010-06-07
forum: Desktop Environments
---

### Post by watchpocket on 2010-06-07
Suddenly, my "Places --> Desktop" folder is identical to my "Places  --> Home Folder".

This happened by accident somehow, and the folders and files in my Home  Folder "/home/rj" are displayed on my desktop, and* I don't want them to  be*.

When I click on "Places --> Desktop" it's as if I've clicked on  "Places --> Home Folder" (the "File Browser" directory opens, the  location is set at "/home/rj", and the title at the top is "File  Browser").

Elementary stuff for a lot of you, I'm sure, but I'm blanking on  how the Desktop folder can be restored to what I'd like it to be  (basically empty, except for a "Downloads" folder), and my folders and  files kept off the actual desktop (except for the "Downloads" folder).

---

### Post by germanix on 2010-06-07
Are these files that are currently in your desktop folder also in your home folder?
If yes, then simply delete these folders that you do not want in the home folder from your home folder.
Are these folders currently not also in the home folder but only in the desktop folder, then simply move  them over to the home folder.

---

### Post by SlidingHorn on 2010-06-07
> **germanix said:**
> Are these files that are currently in your desktop folder also in your home folder?
If yes, then simply delete these folders that you do not want in the home folder from your home folder.
Are these folders currently not also in the home folder but only in the desktop folder, then simply move  them over to the home folder.

I dont think that's the OP's problem.  It seems that when they click Places > Desktop, it opens up their Home directory instead.  I think this can be solved by taking a peek at your ~/.config/user-dirs.dirs (XDG_DESKTOP_DIR variable).  There's more info about that [here]("http://freedesktop.org/wiki/Software/xdg-user-dirs")

---

### Post by watchpocket on 2010-06-14
Still trying to resolve this.

For now I've put a folder named "Desktop" in my home dir, and I've put  all the files and folders that were appearing on the desktop itself  (they're the non-dot files & folders only) in that folder, and I'm  reading through

<http://library.gnome.org/users/user-guide/stable/index.html.en>

xdg-user-dirs (which I had to re-install) hasn't helped much yet.
(Actually I re-installed it and I need to find where it is.)

My ".config/user-dirs.dirs" looks like this:

```
  1 # This file is written by xdg-user-dirs-update
  2 # If you want to change or add directories, just edit the line you're
  3 # interested in. All local changes will be retained on the next run
  4 # Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
  5 # homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
  6 # absolute path. No other format is supported.
  7 #-
  8 XDG_DESKTOP_DIR="$HOME/"
  9 XDG_DOWNLOAD_DIR="$HOME/Downloads"
 10 XDG_TEMPLATES_DIR="$HOME/"
 11 XDG_PUBLICSHARE_DIR="$HOME/Desktop/Public"
 12 XDG_DOCUMENTS_DIR="$HOME/Desktop/Documents"
 13 XDG_MUSIC_DIR="$HOME/Desktop/Music"
 14 XDG_PICTURES_DIR="$HOME/Desktop/Pictures"
 15 XDG_VIDEOS_DIR="$HOME/Desktop/Videos"
```

---

### Post by Timmer1240 on 2010-06-14
[http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/](http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/)     I think this is your answer this exact thing happened to me somehow too!

---

### Post by JustinR on 2010-06-15
Type ALT+F2:

Type "gconf-editor"

Go to: Apps > Nautilus > Preferences

Uncheck the box called: "desktop_is_home_dir"

---

### Post by watchpocket on 2010-06-19
My situation is that files and folders from my home directory appear on the desktop whether I have** desktop_is_home_dir** checked or not.  I've tried it both ways.

They didn't previously appear there, and  I'd like to know how to restore that behavior.

For now, I've put those files & folders that were on the desktop into a folder (on the desktop) named "Desktop".  But when they're in that folder, they don't appear in the File Browser's list of files/folders in my home folder. (I have to open the "Desktop" folder to see them.)

What I want is to see them in the home folder, but not have them appear on the desktop, as was the original behavior.

But checking or unchecking desktop_is_home_dir with gconf-editor has no effect.

---

### Post by watchpocket on 2010-06-19
Turns out that putting all those non-dot files and folders that were on the desktop into a** folder** on the desktop (which is a subdir of my home dir) messes up certain programs (like slrn and sipie) that need to find those files/folders in the home dir, and not in a subdirectory thereof.

So for now I've put all the files/folders [COLOR=Black]**back**[/COLOR] on the desktop and will just have to leave them there until I figure out how to keep them **off** the desktop while still keeping them** in** the home directory.

---

### Post by dasy2k1 on 2010-06-20
> **watchpocket said:**
> Still trying to resolve this.

For now I've put a folder named "Desktop" in my home dir, and I've put  all the files and folders that were appearing on the desktop itself  (they're the non-dot files & folders only) in that folder, and I'm  reading through

<http://library.gnome.org/users/user-guide/stable/index.html.en>

xdg-user-dirs (which I had to re-install) hasn't helped much yet.
(Actually I re-installed it and I need to find where it is.)

My ".config/user-dirs.dirs" looks like this:

```
  1 # This file is written by xdg-user-dirs-update
  2 # If you want to change or add directories, just edit the line you're
  3 # interested in. All local changes will be retained on the next run
  4 # Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
  5 # homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
  6 # absolute path. No other format is supported.
  7 #-
  8 XDG_DESKTOP_DIR="$HOME/"
  9 XDG_DOWNLOAD_DIR="$HOME/Downloads"
 10 XDG_TEMPLATES_DIR="$HOME/"
 11 XDG_PUBLICSHARE_DIR="$HOME/Desktop/Public"
 12 XDG_DOCUMENTS_DIR="$HOME/Desktop/Documents"
 13 XDG_MUSIC_DIR="$HOME/Desktop/Music"
 14 XDG_PICTURES_DIR="$HOME/Desktop/Pictures"
 15 XDG_VIDEOS_DIR="$HOME/Desktop/Videos"
```

the answer to the problem is in your .config/user-dirs.dirs file above

the line that reads 
 ```
 XDG_DESKTOP_DIR="$HOME/"
```

should be 

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

this is hardcoding your desktop dir to be your home dir 
rather than create another folder and shift the stuff you dont want on your desktop create another folder called Desktop, and move all the stuff you **do ** want into that, then change the settings file

---

### Post by watchpocket on 2010-06-20
Thanks -- this worked.  I made the change you suggested and put my Downloads folder inside /home/Desktop/.

(The Downloads folder is the only one I want to see on the desktop itself.)

---

### Post by dasy2k1 on 2010-06-24
if you do that you might want to change 

 XDG_DOWNLOAD_DIR="$HOME/Downloads"
to 

 XDG_DOWNLOAD_DIR="$HOME/Desktop/Downloads"


or better still, keep Downloads in home and in the desktop folder run  the following command

```

ln -s ../Downloads Downloads

```

this will create a link to your downloads folder on the desktop without actually moving the folder from its default location (where most apps will look for it...)

---

