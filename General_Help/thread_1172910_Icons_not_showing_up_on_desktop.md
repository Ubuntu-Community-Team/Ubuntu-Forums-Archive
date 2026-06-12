---
title: "Icons not showing up on desktop"
date: 2009-05-29
forum: General Help
---

### Post by Sentience on 2009-05-29
I seem to have another problem. None of my icons are showing up on my desktop. This started happening on my laptop and on my desktop at the same time. I cant figure out what could be causing this besides maybe a torrent that I downloaded and transfered to the other computer.

WTF?

Any tips on this to try to where to start looking for solutions?

---

### Post by nothingspecial on 2009-05-29
Press Alt F2 and type ```
gconf-editor
```

Go to apps > nautilus > preferences and check if show desktop is checked. 
That might be it.

---

### Post by Sentience on 2009-05-29
Show desktop is checked and set to true. Still no icons on the desktop, but I can find them when I open the desktop in a folder.

---

### Post by Sentience on 2009-05-29
Any more ideas?

This happened to both computers at the same time. Could it have something to do with the external hard drive they share or perhaps with a file I downloaded from torrent?

I also noticed that my trash folder wouldnt delete, then shortly after it finally did, my desktop icons were gone.

---

### Post by Sentience on 2009-05-29
So I open my trash folder and all my icons come back.

Weird.

---

### Post by CatKiller on 2009-05-29
> **Sentience said:**
> So I open my trash folder and all my icons come back.

Weird.

Not that weird. It's Nautilus (the default file manager) that draws the icons on the desktop. If you launch Nautilus, it will draw the icons on the desktop again. Most of the shortcuts - Home folder, Computer, and so on, start nautilus with the --no-desktop option to stop it re-drawing the icons every time you open a new window. AFAIK, the Wastebasket shortcut doesn't specify the --no-desktop option.

---

