---
title: "How do I remove desktop icon left from Maverick?"
date: 2011-04-25
forum: Desktop Environments
---

### Post by rscow on 2011-04-25
I was using Maverick.  I created a desktop icon for the trash and placed it on desktop.  Then removed the one from the taskbar.

Now I'm running Natty Beta and the trashcan icon is still there.  It is also in the Unity task bar.  

I want to get rid of the one I created, but can't figure out how.  I can't drag to trash, right click only gives properties.  The menu item from desktop "Customize toolbar" doesn't work.  Looked at gconf-editor no luck.  

Suggestions?

Thanks,
Roger

---

### Post by KegHead on 2011-04-25
Hi!

If I understand,You can use Natty classic if you want to get rid of the task bar.

system..admin...login..

choose "classic.

Restart.

KegHead

---

### Post by Copper Bezel on 2011-04-25
No, I think you misread him. = )

There are two possibilities, rscow, depending on how you put the trash can there in the first place. One is indeed in gconf-editor, under apps -> nautilus -> desktop; make certain the trash_icon_visible key is not checked. You may need to restart Nautilus to get the setting to apply by running [FONT="Courier New"]killall nautilus[/FONT] .

The other possibility is that you created a launcher for Trash. If that's the case, you should have been able to delete it from the desktop, but if the key I mentioned above is unchecked and that option just isn't displaying for some reason, browse to your Desktop folder (you can just run [FONT="Courier New"]nautilus Desktop[/FONT]) and delete the launcher there.

---

### Post by rscow on 2011-04-25
Thanks, Copper Bezel and KegHead.

I ran gconf-editor and found the right entry (under Nautilus Desktop).  Unticked the box and poof.

THanks again!

Roger

---

