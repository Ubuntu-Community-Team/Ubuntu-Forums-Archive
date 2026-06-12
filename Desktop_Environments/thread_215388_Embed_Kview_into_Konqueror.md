---
title: "Embed Kview into Konqueror"
date: 2006-07-13
forum: Desktop Environments
---

### Post by McSnuffy on 2006-07-13
After installing Ubuntu, I decided to get KDE. However, I didn't want KDE clones of all my GNOME apps, so I got the kde-core package, thinking that I would just download anything else I needed later. I soon noticed that Konqueror didn't have its nice embedded image viewer. I got Kview, but I have no idea how to embed it into Konqueror, instead of having it open in another window. Any ideas on how to make this work?

Thanks for your time.

---

### Post by Jucato on 2006-07-13
If you installed kubuntu-desktop over Ubuntu, GwenView, the default Kubuntu/KDE image viewer, should be installed, too. AFAIK, this is what Konqueror now uses to preview images.

You can use the embedded viewers (not just for images) by right-clicking on the file and choosing Preview. But you can also set "Show file in embedded viewer" as the default left-click action for certain file types. To do this, go to Konqueror > Settings menu > Configure Konqueror > File Associations > image groups > use "Show file in embedded viewer" as the default. 

If you don't want to use the default embedded GwenView for previewing images, you can change this by searching the individual image types, going to the Embedding tab, and Adding or Moving up the KPart/Embedded viewer that you want.

---

### Post by McSnuffy on 2006-07-14
I went into the settings menu and I was able to associate the images with Kview. Now they show up embedded and everything. Thanks a lot.

---

