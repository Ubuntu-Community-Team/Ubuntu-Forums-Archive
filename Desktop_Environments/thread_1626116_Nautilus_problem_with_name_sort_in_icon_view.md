---
title: "Nautilus: problem with name sort in icon view"
date: 2010-11-19
forum: Desktop Environments
---

### Post by mps_1 on 2010-11-19
Hi everybody

I have a problem with Nautilus. In *gconf-editor>apps>nautilus*, for icon view I have chosen sorting by name and show-folders-first, but the sorting follows an order that I can't understand. It is not alphabetical. Nautilus is sorting reversly by date_modification (you can see the image attached). Also, it merges folders and files, although I choose folders first. When I change different sorting schemes (reverse, sort by date, etc) nothing happens in the appearance. Have you got any suggestion?

---

### Post by asmoore82 on 2010-11-20
The key in gconf sets the default sort order for newly navigated folders,
Nautilus will still remember the last sort state of each folder separately.

You can force nautilus to forget this info by deleting files in
"$HOME/.local/share/gvfs-metadata" and then restart nautilus.

But I'm not sure what else the files in there do!

EDIT: It really annoys me when people make crazy suggestions without
trying them out themselves. I'm happy to report that I do test my insane
suggestions. **By the way, [COLOR="Red"]deleting these files is probably not a good idea![/COLOR]**

---

### Post by mps_1 on 2010-11-20
Thanks for your prompt response. 

the tip didn't work. I moved the content to a new folder, but the sorting scheme remained and the files were created automatically when I started nautilus again. But... this help me to realize that some folders had this problems and others didn't. So I went to "organize elements by..." and solved the problem for each folder individually. But I couldn't find where these configurations are saved.

Thanks again

---

