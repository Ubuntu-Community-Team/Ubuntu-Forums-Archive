---
title: "Changing documents folders MOVED my stuff!"
date: 2010-01-19
forum: Desktop Environments
---

### Post by cmulcahy on 2010-01-19
Here's an odd one.  I was having severe KDE stability problems so moved to Gnome for a year.  I decided to just go ahead and rename my ~/.kde directory and try KDE out again.  All went well with a fresh install.  

It was as I was configuring my new environment that my system tried to give me a heart attack.  Nearly worked, too!  

I was changing where KDE looks for Documents, Pictures, Music, etc.  For some reason, KDE moved all of my home directory contents to new places.  

I have a /music directory that is symlinked into my home directory (to make sharing music easier with other users on the system).  My symlink was deleted and replaced with a physical Music directory.  MOST of my home directory contents were moved to /music.  Some of my content was moved to my ~/Downloads directory.  My ~/Desktop directory was moved to be a sub of ~/Downloads.  Basically, it scattered everything I had in ~ thoughout my filesystem.  I'm sure there's a pattern and a reason but I'll be damned if I can figure it out.  

Is this a "stupid user" issue on my part?  Is there a bug in KDE as it relates to special document directories?

Lastly, which config file holds reference to these directories so I can edit the file directly (~/music instead of ~/Music) and hopefully avoid having my files strewn throughout creation?

Thanks in advance.

---

### Post by Zorael on 2010-01-19
There's actually a dialog that pops up when you change the paths, asking if you want to move your old content to the new directories. So in a sense it's per design.

The file where such directories are defined is at **~/.config/user-dirs.dirs**. The system-wide "template" given to new users is at **/etc/xdg/user-dirs.defaults**. It should be an environment-unspecific setting, so what you set up in GNOME should transfer to KDE.

---

### Post by cmulcahy on 2010-01-20
That makes perfect sense.  I did not see that dialog asking if I want all of my stuff scattered around the filesystem but it was early in the morning.  Perhaps I did not have enough coffee in me yet.  

Thanks for the info.  It sounds like a likely explanation.  Anyway, I found all of my files and put them back where they belong.  It's all good again.

---

