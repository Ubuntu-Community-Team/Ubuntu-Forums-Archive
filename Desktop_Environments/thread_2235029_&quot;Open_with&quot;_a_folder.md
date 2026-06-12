---
title: "&quot;Open with&quot; a folder"
date: 2014-07-18
forum: Desktop Environments
---

### Post by claudiorv89 on 2014-07-18
Hello. I was using Ubuntu 12 but now Im with 14. Now I cant open a folder with, for example, Audacious if I want to listen the music. In all individual files I can "open with" my programs, but not in the folder. If I right click a folder I cant see the "open with" option. Can we fix it? Thanks!

---

### Post by Dennis N on 2014-07-18
"Open with > [application]" in the file manager is only possible when you select a file (not a folder). Use Audacious' add files functionality to add a complete folder of music to the play list by:  **Audacious File Menu > Add Files (or click the "+" on it's toolbar)** then browse to the desired music folder, highlight it, and click on the "+Add" button.

---

### Post by ajgreeny on 2014-07-18
You can use the Open folder (or directory) in gnome-mplayer and vlc, and perhaps others, but not using audacious, even in 12.04, which you suggest was possible.

---

### Post by Dennis N on 2014-07-18
> **ajgreeny said:**
> You can use the Open folder (or directory) in gnome-mplayer and vlc, and perhaps others, but not using audacious, even in 12.04, which you suggest was possible.

No, it is definitely possible. I do this all the time. Use either:

1) File > Open Files > Browse to select folder  and click Open (this is equivalent to using the "open file" icon on the toolbar)
2) File > Add Files > Browse to select folder and click Add (this is equivalent to using the toolbar "+")

The difference is, (1) will clear the playlist before adding the music files in the folder, while (2) will append the files in the folder to the playlist.

---

### Post by ajgreeny on 2014-07-18
> **Dennis N said:**
> No, it is definitely possible. I do this all the time. Use either:

1) File > Open Files > Browse to select folder  and click Open (this is equivalent to using the "open file" icon on the toolbar)
2) File > Add Files > Browse to select folder and click Add (this is equivalent to using the toolbar "+")

The difference is, (1) will clear the playlist before adding the music files in the folder, while (2) will append the files in the folder to the playlist.
Well I never! So it does!

I admit I was not aware of that.

---

### Post by mc4man on 2014-07-18
I had a bug report on this for quite some time, eventually no longer cared about the report & just ppa'd the fix.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254)

For trusty 2 other patches are included as some requested (I have about 8 nautilus patches & aren't going to do seperate ppa's for each.
So here you'll get open with on folders back plus a parent button & the inconsequential real name for file owner instead of the nonsense "Me"
[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open)

(- if you just want open with returned then the ppa source contains the patch (debian/patches/open-with1.patch

---

### Post by Dennis N on 2014-07-19
To make sense, wouldn't "**open folder** with <application>" then really have to mean "**open files in the folder** with <application>"? ( <application> being some other application than another file browser.)

PCManFM has this "open with" in its folder context menu, and I can choose Audacious, but Audacious is really only opening files in the folder.
 
(This works well in PCManFM and a folder of music files. But not with a folder of six .odt files (open document) and using "open with" Libre Office Writer. LO displayed its splash screen, then crashed every time.)

Also note that Thunar does not offer "open with..." for folders either.

---

### Post by claudiorv89 on 2014-07-19
With Ubuntu 12 I could do right click in a folder and "open with" Audacious, VLC, etc. What I don want is have to select the content, but Dennis N have the solution :)

---

### Post by Dennis N on 2014-07-19
Hi claudiov89,

Checking the three file-managers I am acquainted with (Nautilus, Thunar, PCManFM) only PCManFM will do this from the file manager.

If the issue is resolved, you can use "Thread Tools" at the top to mark it as solved.

---

