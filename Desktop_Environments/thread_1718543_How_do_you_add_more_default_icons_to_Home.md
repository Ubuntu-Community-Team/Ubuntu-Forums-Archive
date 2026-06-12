---
title: "How do you add more default icons to Home"
date: 2011-03-31
forum: Desktop Environments
---

### Post by N00b-un-2 on 2011-03-31
I use Hydroxygen as my icon theme which is a very polished and complete icon set.  I'd actually say it's even more so than Humanity is, and it's highly customizable.  It includes a lot of awesome folder icons for the folders in your home directory (Documents, Pictures, etc.) which do not automatically replace the ones in Humanity.  After A LONG time researching this, I discovered it has something to do with XDG and how XDG looks for default folders at boot up.
There is abysmally little documentation on how to use XDG which is why I'm stuck here now.  By sym linking and renaming the proper icons in Hydroxygen to match the naming scheme that XDG looks for, I've been able to set the custom icons to the DEFAULT FOLDERS ONLY.
ie; Documents, Pictures, Music, Videos, Downloads, Public

Now I'm stuck though.  I've added two folders -- $HOME/Scripts and $HOME/Games to both the files ~/.config/user-dirs.dirs and /etc/xdg/user-dirs.defaults.
It is my understanding that doing so should cause XDG to look for icons named 'folder-scripts.png' and 'folder-games.png' under the /places folder in the icon theme I'm using and assign them to the corresponding folder in the $HOME directory -- which DID work for all the default folders.  However, I'm unable to add additional folders.

If anyone can help me out here, it would be greatly appreciated.

---

