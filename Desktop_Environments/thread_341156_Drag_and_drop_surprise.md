---
title: "Drag and drop surprise"
date: 2007-01-18
forum: Desktop Environments
---

### Post by frisket on 2007-01-18
In Edgy I opened the File Browser and navigated to a folder where I had a file I wanted to upload to a web site by FTP. I wanted to test the in-browser upload (not using a plug-in).

I ran Firefox and went to [ftp://username: password@www.host.domain/directory](ftp://username: password@www.host.domain/directory) and it opened the remote web site directory. I clicked on a file in by File Browser and dragged it into the Firefox window...and Firefox opened the local file instead of uploading it to the web site!

This may be deliberate on the part of FF, or just ignorance of the conventions of cross-window file traffic, but it's certainly unexpected, and definitely not what plain users expect.

I don't know if this is a Gnome problem, a Firefox problem, or an Ubuntu problem. Where should I look for a solution, if there is one?

---

### Post by zanglang on 2007-01-18
More likely... not a problem, but a feature that has been brought up before, but decided as "not going to implement" by the Firefox devs. I think I've seen a thread somewhere on their Bugzilla that discussed this. After all, Firefox is a "web browser", not an all-purpose platform.

You might want to try using Nautilus to directly access the directory, or download a separate GUI app like Gftp. ;)

---

### Post by frisket on 2007-01-22
> **zanglang said:**
> More likely... not a problem, but a feature that has been brought up before, but decided as "not going to implement" by the Firefox devs. I think I've seen a thread somewhere on their Bugzilla that discussed this. After all, Firefox is a "web browser", not an all-purpose platform.

You might want to try using Nautilus to directly access the directory, or download a separate GUI app like Gftp. ;)

I thought it might be something like that. The argument is of course completely specious, a bit like saying OO is a wordprocessor, so we're not going to let people drag and drop files onto it. As usual, the devs -- no matter how brilliant at writing a browser -- are living on a different planet to the rest of us. 

The objective is to let the user upload a file to their web site *without* the need for a separate FTP application. Unfortunately, MSIE *does* provide this drag-and-drop functionality, so we will continue to recommend it, which is a pity.

---

