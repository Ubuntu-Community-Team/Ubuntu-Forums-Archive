---
title: "People that use &quot;~&quot; in folder names ARGH"
date: 2006-10-25
forum: Desktop Environments
---

### Post by Aikon- on 2006-10-25
Wow, I hate people that have folders containing the character "~" inside of RAR files...

I had about 25 RAR files that I wanted to unpack in-place, so I selected them all and clicked "Extract here"... Kept running into a problem where some folders wouldn't show up.

After a while, I went into the command prompt and found that the missing folders **were in fact there**, its just that the folder names contained the "~" character. This prevented them from showing up in Nautilus, even though they showed up fine with a simple ls command.

Renaming these rogue folders to eliminate the ~ caused them to appear instantly in Nautilus.

Moral of the story: DON'T USE ~ IN RAR FILES!!!!!!!! OR ANYTHING ELSE!!

/sigh.....

---

### Post by jazzgossen on 2006-10-26
Actually, the moral of the story should be to file a bug for Nautilus. This can't be the desired behaviour, right?

---

### Post by Titus A Duxass on 2006-10-26
I've got a ~ on my keyboard and I'm not afraid to use it!

---

### Post by RoyArne on 2006-10-26
> **jazzgossen said:**
> Actually, the moral of the story should be to file a bug for Nautilus. This can't be the desired behaviour, right?

Editors like emacs create a copy of the file they are editing and appends a "~" character to the file name to mark the copy as a backup. I think Nautilus hides these files to prevent clutter.

---

### Post by stilus on 2006-10-26
nautilus has a "view hidden" option, though I'm not sure what the shortcut to it is (ctrl+H?). it not only shows the "~" files but also the ".abcde" files and hidden folders. 

Good luck!

stilus

---

### Post by Aikon- on 2006-10-26
> **RoyArne said:**
> Editors like emacs create a copy of the file they are editing and appends a "~" character to the file name to mark the copy as a backup. I think Nautilus hides these files to prevent clutter.

Yes.. shortly after I ranted about this to my friend via MSN (well, GAIM.. but I still call it MSN..... come to think of it, we were both using GAIM, and it was over Jabber using the gtalk servers, so I gues MSN is really really REALLY a misnomer) he was like "oh ya.. ~ == hidden I think, try CTRL-H" and sure enough it worked.

But still, ~ in folder  names in RAR files is mean, just like any other special character (I had a hell of a time fixing a bunch of folders that used !, just try to get Bash to play nicely with THAT!)

---

### Post by FyreBrand on 2006-10-26
Another reason you might see a tilde "~" in a file or path name is that if the rar was created in an MS-DOS command line type of environment names longer than 8 characters will be truncated and appended with a ~.  It's a really annoying feature of old DOS that still lingers.  Sometimes when I take a file home from work or school I will have to fix the names.

---

