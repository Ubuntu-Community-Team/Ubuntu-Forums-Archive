---
title: "How to remove Google Desktops from Gadget list"
date: 2009-02-02
forum: General Help
---

### Post by nfox on 2009-02-02
If you've dabbled with Google Gadgets in KDE 4, you probably want to be able to remove them as well. I want to make an ongoing tutorial here on playing with Gadgets so please give me feedback so I can update it. I like the GG idea because I'm not planning on learning C++ or Python and web-scripting is second nature for me to make my own.

*******************************************************************************************
I use KDE4.2 nightly built from trunk off of a server install-- no KDE4.1 stable on my box. Your folder may be slightly different but should be similar. Generally, I think you remove ".kde-neon" with ".kde4" so please correct me if I'm wrong.

**~/.kde-neon/share/kde4/services/**

Delete the .desktop entries and they will be removed from the list immediately (you don't have to close the Add Gadgets window for it to refresh). As far as where the actual files are saved, I believe it's:

**~/.kde-neon/share/apps/plasma/plasmoids/**

But there are some other folders as well that have thumbnails and other entries. 

Please post your experience so I can keep this up to date. I want references to adding and cleanly removing Google Gadgets, OS X and plasmoids as well as development.

---

