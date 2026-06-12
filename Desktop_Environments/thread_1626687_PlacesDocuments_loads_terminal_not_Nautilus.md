---
title: "Places/Documents loads terminal not Nautilus"
date: 2010-11-20
forum: Desktop Environments
---

### Post by donskn on 2010-11-20
I was trying out bash scripts to see how to mount NetGear readyshare. I can do so using Nautilus and selecting Network but I wanted to be able to do so from a script. I don't know how it happened but when I clicked on [FONT=Courier New]Places/Documents[/FONT] it opened a terminal instead of Nautilus. This applies to all the folders in the Places menu but I can still get Nautilus by clicking [FONT=Courier New]Places/Computer[/FONT] and below.

I've spent several hours googling and haven't found anything that looks remotely like dealing with the problem, can anybody give me any clues?

I'm using ubuntu 10.4, nautilus 2.30.1

Don

---

### Post by sikander3786 on 2010-11-20
Right click your desktop. create a new folder if you don't have one already.

Right Click the folder > Open with other application > Select File Browser > Tick the box for "Remember this application for 'folder' files > Open.

---

### Post by donskn on 2010-11-21
> **sikander3786 said:**
> Right click your desktop. create a new folder if you don't have one already.

Right Click the folder > Open with other application > Select File Browser > Tick the box for "Remember this application for 'folder' files > Open.

I came across this proposal in my initial research. It does give me easy access to Nautilus but it doesn't solve the problem. After I have gone through this process clicking on **[FONT=Courier New]Places [/FONT]**in the top panel and then clicking on **[FONT=Courier New]Doc[/FONT][FONT=Courier New]uments[/FONT]**  still opens a terminal, not Nautilus displaying the Documents folder.

Don

---

### Post by sikander3786 on 2010-11-21
Ok then this might apply to you as well.

[http://ubuntuforums.org/showpost.php?p=7435286&postcount=5](http://ubuntuforums.org/showpost.php?p=7435286&postcount=5)

---

### Post by donskn on 2010-11-23
> **sikander3786 said:**
> Ok then this might apply to you as well.

[http://ubuntuforums.org/showpost.php?p=7435286&postcount=5](http://ubuntuforums.org/showpost.php?p=7435286&postcount=5)


Thanks very much. That looks promising and something to get my teeth into.

Don

---

### Post by donskn on 2010-11-28
> **sikander3786 said:**
> Ok then this might apply to you as well.

[http://ubuntuforums.org/showpost.php?p=7435286&postcount=5](http://ubuntuforums.org/showpost.php?p=7435286&postcount=5)

file associations are found in ~/.local/share/applications/mimeapps.list
mine had the entry (all on one line):
inode/directory=userapp-gnome-terminal-ONTSKV.desktop;nautilus-folder-handler.desktop;nautilus-browser.desktop;

I changed it to:
inode/directory=nautilus-folder-handler.desktop;nautilus-browser.desktop;

and that **solved the problem**.

Thanks for the pointer. Sorry to be so long replying, but it turned out simpler than I feared!

Don

---

