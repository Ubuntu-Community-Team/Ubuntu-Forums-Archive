---
title: "Files app -- How to remove Music/Videos/Pictures items from sidebar"
date: 2017-10-24
forum: Desktop Environments
---

### Post by igouy on 2017-10-24
Ubuntu 17.10 Files app

I can delete the folders from ~ but that doesn't seem to remove them from the Files (? Nautilus)  sidebar, the broken links are still there?

[HR][/HR]

[http://jamesmcminn.com/2012/12/removing-entries-from-nautilus-3-6-places/](http://jamesmcminn.com/2012/12/removing-entries-from-nautilus-3-6-places/)

---

### Post by owlcroft on 2017-12-04
I have just installed 17.10 and am having the same problem.  Cannot someone help us out here?

---

### Post by vanadium on 2017-12-05
I do not know about possible side effects, but if you comment the folders out in .config/user-dirs.dir, the folders appear as "normal" bookmarks that can be deleted. Of course, this ceases to make these "special" folders, but that would not be a problem as you delete them after all.

---

### Post by entropy1 on 2017-12-06
As an alternative to commenting out those lines, just remove the folder name at the end of the path name:
[HTML]XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"[/HTML]

Now my sidebar does not show anything for Templates, Public, Music, Pictures, or Videos --- not even an empty line.

---

