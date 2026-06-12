---
title: "Editting 'Places' in ume-launcher"
date: 2008-12-14
forum: Desktop Environments
---

### Post by sgrabowski on 2008-12-14
Can anyone tell me of a way to edit the 'places' section of the ume-launcher in Netbook-Remix (Hardy)?

There seems to be a bug; I made a folder and added it to the places toolbar by drag-and-drop, but I deleted the folder before removing the places link. This removed it from nautilus, but the link remained on the launcher. I've done this twice now and thus now I have two dead links I cannot remove.

Screenshot: [Link]("http://www.sgrabowski.co.uk/uploader/Screenshot.png")

I've tried reinstalling ume-launcher - using purge to remove configs. To restart I used the command line and I got this output:
```
** (ume-launcher:5650): DEBUG: Font dpi: 96
** (ume-launcher:5650): DEBUG: Font changed: Sans 10

** (ume-launcher:5650): DEBUG: Connecting to ConsoleKit for suspend/resume restarting
Not themed icon: file:///media/ORIETA/OOO300_m9_native_packed-1_en-US.9358/DEBS/untitled%20folder
Not themed icon: file:///home/stefan/Downloads/OOO300_m9_native_packed-1_en-US.9358/untitled%20folder
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Not themed icon: file:///media/ORIETA/OOO300_m9_native_packed-1_en-US.9358/DEBS/untitled%20folder
Not themed icon: file:///home/stefan/Downloads/OOO300_m9_native_packed-1_en-US.9358/untitled%20folder

*[...]*

seahorse nautilus module shutdown

(ume-launcher:5650): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.


(ume-launcher:5650): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.


(gimp-2.4:5672): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkFileFolder'

(ume-launcher:5650): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.

seahorse nautilus module initialized
Initializing nautilus-share extension
Not themed icon: file:///media/ORIETA/OOO300_m9_native_packed-1_en-US.9358/DEBS/untitled%20folder
Not themed icon: file:///home/stefan/Downloads/OOO300_m9_native_packed-1_en-US.9358/untitled%20folder
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[...]

```

The folder error just continues until I kill it. I think this is hitting performance too.

Any help is much appreciated! This is my first post so if its in the wrong place etc please move!

Stefan

---

### Post by sgrabowski on 2008-12-15
Found the answer by trying to sort something else out... it seems that the ume-launcher does not hide dead places links like nautilus. The only solution is to load nautilus > edit bookmarks > and then the dead links are shown with a globe and question mark icon. Simply remove and then they are gone from the launcher.

Quick solution to something that had bugged me for days.

---

