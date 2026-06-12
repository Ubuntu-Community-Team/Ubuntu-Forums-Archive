---
title: "Window for folder freeze upon opening"
date: 2009-03-04
forum: Desktop Environments
---

### Post by joey_breizh on 2009-03-04
For a few days now I've been having a problem with one of my folders. When I click to open it (whether from the desktop or from the left side of the file browser), it freezes so I have to force quit and restart nautilus. It has been doing it systematically with one of my folders, but just this one.

I tried replacing .gconf in my home folder (created a .gconf.old then restarted) and this fixed the problem. But it also returned my computer to its original customization. It's taken me a while to customize everything and I would rather not lose all of it.

So I was wondering if anyone knows how to locally solve this issue? Could I simply cut and paste the content of the folder into a new folder and erase the one causing problems? (If yes, how do I cut and paste everything when I don't have access to the folder?)

Thanks for your help!

---

### Post by kanikilu on 2009-03-04
Do you have any trouble browsing that directory from the terminal? What about trying an alternate file manager like PCManFM (sudo apt-get install pcmanfm).

It might also be worth checking the filesystem (fsck) or even running the hard drive diagnostic tool from the manufacturer of the disk. UBCD also has some hard drive diagnostic tools.

---

### Post by joey_breizh on 2009-03-04
Thanks for your quick reply! I can access the folder in the terminal without any problem... and I've just installed PCManFM and it seems to be working just fine, so thank you for the tip! 

I just wish I could understand why a folder that's not corrupted and can be access via the terminal would react like this in nautilus...

---

### Post by kanikilu on 2009-03-04
If you don't mind me asking, what kind of files are in that directory? If they are media files (images, music, etc.), you might want to try changing the preview settings in nautilus. 

Edit > Preferences > Preview tab

Maybe try setting all dropdowns to "never" and then if that works, work your way up from there (or just leave previews turned off if you don't need them).

---

### Post by joey_breizh on 2009-03-04
Definitely a media folder, and I just turned off the previews like you said, and the folder seems fine now! Thank you so much, this is great.

Thanks again for your help!

---

### Post by kanikilu on 2009-03-04
Hmm, I'm not sure. I'm able to create pretty long names before they wrap to a new line.

Is your Zoom level set to 100%? Go to View > Normal Size to reset it.

I'm not sure if that's problem though...I played around with that on mine and couldn't get it to wrap as low as 6 characters...

---

### Post by joey_breizh on 2009-03-04
I had "compact view" selected in the options, that's where the problem was coming from. Deselected that and it's all good now! Thanks :)

---

