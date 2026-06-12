---
title: "changing location of music folder?"
date: 2009-04-30
forum: General Help
---

### Post by rose34 on 2009-04-30
Hi,

I have recently installed an external hard drive, and copied all my music to this. Is it possible to change the location in the drop down Places menu at the top of the screen, so that it opens this folder rather than the Music folder in my home folder?

I hope this makes sense...

cheers,
Joe

---

### Post by SentientFluid on 2009-04-30
I'm not at my computer right now but have you tried removing the Music folder from your Home folder and replacing it with a link to your new Music folder?

---

### Post by blackened on 2009-04-30
The music folder in the places menu is only a bookmark. All you have to do is delete the original bookmark, then bookmark your new folder and it will show up. You can even have both bookmarked if you feel like.

---

### Post by mb_webguy on 2009-04-30
> **SentientFluid said:**
> I'm not at my computer right now but have you tried removing the Music folder from your Home folder and replacing it with a link to your new Music folder?

+1

If you've emptied out the Music folder in your home directory, delete it with "rm ~/Music", then create a link to the new Music location with "ln -s /path/to/new/Music ~/Music".

---

### Post by SentientFluid on 2009-04-30
> **mb_webguy said:**
> +1

If you've emptied out the Music folder in your home directory, delete it with "rm ~/Music", then create a link to the new Music location with "ln -s /path/to/new/Music ~/Music".

Rather than go to the Terminal you can do it from the GUI:

1. Right click the folder you want to delete and Move to Trash. Empty the Trash if you know you don't need it anymore.  This is better than using rm ~/Music as rm deletes it permanently so there's no chance of recovery if you made a mistake.

2. Right click your "new" Music folder, choose Make Link, then copy and paste the link into your Home folder.

3. Right click the link that is now in your Home folder and choose Rename.  Rename it to Music... or whatever else you'd like.

---

