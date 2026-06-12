---
title: "New cursor theme and Firefox help needed"
date: 2008-12-30
forum: General Help
---

### Post by BigSilly on 2008-12-30
Having a play with my themes, and got a nice new look all set up. However, I cannot seem to get Firefox to play nice with my new cursor theme. I've only selected the whiteglass cursor from the Appearance menu, and it's fine with everything else, but when FF is busy (i.e. downloading a new page etc) it seems to default to the usual DMZ cursor briefly. I don't use use Compiz, but I do have it installed so I changed it's settings to use the new cursor as many advise, but it's made no difference.

It's silly I know, but pretty annoying, especially as it seems such a simple thing. Is there any way to get Firefox to only use my selected cursor theme?

Thanks all. :)

---

### Post by GeorgeMurango on 2008-12-31
If you've only just selected the new cursor, you need to log out and back in to restart the desktop. Your new cursor theme isn't fully loaded yet. I've had the same problem. Hope that helps.

---

### Post by BigSilly on 2008-12-31
Thanks, but I forgot to mention that I did that too and it didn't make a difference.

I can't imagine what I should do to make the changes complete. If anyone knows please tell me!

Thanks again.

---

### Post by Ivo Moelans on 2008-12-31
It has something to do with the naming convention in the cursor theme. Some apps expect a different name for the same cursor picture. Whiteglass lacks a few, but that can be solved with symlinks. I packed most if not all of them in the attached file.

Download and unpack. Put the files of the folder in */usr/share/icons/whiteglass/cursors*. You'll need to be root for that: *gksudo nautilus /usr/share/icons/whiteglass/cursors*. Logout & login. That should do it.

Let me know if this helps.

Edit: see post 6

---

### Post by BigSilly on 2008-12-31
Thanks for your reply, but there doesn't appear to be anything in the folder once I'd unpacked it. Have I done something wrong? I just used the archive manager to extract it. Thanks.

---

### Post by Ivo Moelans on 2008-12-31
Apparently you can't compress a folder with links without their corresponding files...
So I compressed a complete cursor theme that as far as I know is complete.
Unpack the theme an go in the subdirectory *cursors*. Copy *only* the files that are links (in nautilus, list view, column *Type*). A few files/links will already be in the theme: skip those. You get the idea: it is a matter of completing the theme with missing references.

---

