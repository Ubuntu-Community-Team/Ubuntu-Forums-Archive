---
title: "Missing Folders/Files in Nautilus - Hardy Heron"
date: 2008-07-12
forum: Desktop Environments
---

### Post by Drakar_Noir on 2008-07-12
Greetings,

Fairly new user, first post, my appologies if this is improperly posted, guidance and constructive criticism gladly received!

Ubuntu 8.04 installed and running well. About a week ago (or at least that is when I noticed this problem) Nautilus stopped displaying all the files and folders on a second internal HDD.  Both GNOME Commander AND Krusader "see" and display (and open, delete, etc.) all of the folders and files on the drive.

Also, if I reboot into Ubuntu 7.04, Nautilus "sees" and displays )opens, deletes, etc.) all of the folders and files.

Any ideas?  I have searched the forums and googled the issue.  Perhaps I am unsure of what I am really searching for! 

Any help would be greatly appreciated.

---

### Post by coffeecat on 2008-07-12
Are these 'hidden' files? Hidden files have a leading dot, E.g.: .fonts, not fonts.

The default nautilus behaviour is not to show hidden files, but you can enable showing them with ctrl-H or (from the menu) View > Show Hidden.

If this is not the case, could you post a couple of screenshots so we can see what's going on? PrtSc for a complete desktop; Alt+PrtSc for just the focussed window.

---

### Post by Drakar_Noir on 2008-07-12
coffeecat,

Thanks forthe reply...here is the info (I hope) that you requested.

No the folders/files in question are not hidden files.  I have Nautilus set to show them anyway.

Here are the screen shots:

Nautilus:
[IMG]http://www.livingstonemi.com/pics/1.png[/IMG]

GNOME Commander
[IMG]http://www.livingstonemi.com/pics/2.png[/IMG]

I can show the screen shots from Feisty if needed...though I would need to reboot.

---

### Post by coffeecat on 2008-07-12
Oo-er :? I see what you mean. I have no idea. One thought though. Gnome Commander is stating that there are 353 directories 'selected'. Would that be 353 folders in your My Music drive/partition/whatever? But nautilus is saying '107 items', so presumably it is only showing 107 of those folders. I've never encountered a limitation with the number of files that nautilus can display, but is it possible that Nautilus gets confused when there are over a certain number of directories? Could this be a Nautilus bug? I don't know the answer to that but 353 is certainly a helluvalot of folders. Do you buy them by the score or the dozen? :wink:

I'm intrigued. I'll do a bit of googling but I offer that thought in the meantime.

---

### Post by Drakar_Noir on 2008-07-12
By the Gross!

I am as confused...as I stated prior, in Feisty Nautilus displays and manipulets ALL the folders/files!

Thanks for the input...awaiting further info and am continuing to look myself.

---

### Post by coffeecat on 2008-07-12
> **Drakar_Noir said:**
> as I stated prior, in Feisty Nautilus displays and manipulets ALL the folders/files!

Ah yes, but Feisty was using an earlier version of Gnome/Nautilus. The Gnome devs managed to introduce one nasty little bug into the 2.22 version of Nautilus (as used in Hardy) which wasn't there before. Perhaps they've introduced others.

The one I'm referring to is the failure of Nautilus to preserve timestamps on a drag and drop copy from one window to another. It affected all filesystem types. It's been fixed in Ubuntu now but not Suse and Mandriva - at least not when I last looked.

**Edit:** I'm cross-posting something I've posted on [this thread](http://ubuntuforums.org/showthread.php?p=5370521#post5370521), but I'm sure the mods won't mind. :wink: It sounds like a similar issue. I think there may indeed be a Nautilus bug. Can I suggest you two compare notes? I'll just sit back and listen in if that's all right. :p

---

### Post by Drakar_Noir on 2008-07-12
Perhaps...

on my other box (same version of Ubuntu) it appears that Nautilus can see and manipulate well over 300 folders/files (redundant backup of music).

Perhaps I have a glitch in my install...I think I shall reinstall on this box.

---

### Post by coffeecat on 2008-07-12
Checkout my edit first. :) You posted and I edited simultaneously.

---

### Post by Drakar_Noir on 2008-07-12
Thanks...seems to be a similar problem.

However, the fact that my other box seems to function properly throughs me a NEW curve!

---

### Post by rengolin on 2008-07-21
Hi Drakar,

I've got the same problem and fixed it. The problem was that the files on

~/.gconf/apps/nautilus

didn't work with the new 2.22 Nautilus release. Just kill it (or move to a .bkp) and restart Gnome. That should do it.

The new nautilus package should've taken care of it automagically anyway.

cheers,
--renato

---

