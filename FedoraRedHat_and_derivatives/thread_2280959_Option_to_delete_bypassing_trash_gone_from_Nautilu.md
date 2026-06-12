---
title: "Option to delete bypassing trash gone from Nautilus??"
date: 2015-06-03
forum: Fedora/RedHat and derivatives
---

### Post by monkeybrain20122 on 2015-06-03
Just installed Fedora 22 gnome shell and noticed that in File >  Preferences > Behavior  the option to delete bypassing trash has disappeared. Can anyone confirm this?? I hate the idea of trash. When I remove something I want it gone, not to be moved to a hidden folder!

---

### Post by buzzingrobot on 2015-06-03
Install dconf-editor and try unchecking 'org.gnome.nautilus.preferences.confirm-trash'. It does not delete without asking, it just moves to Trash without asking.

I haven't looked for a way to restore an actual Delete function.

---

### Post by monkeybrain20122 on 2015-06-03
> **buzzingrobot said:**
> Install dconf-editor and try unchecking 'org.gnome.nautilus.preferences.confirm-trash'. It does not delete without asking, it just moves to Trash without asking.But now the bypassing trash option appears to be missing and it is stupid  to have to use the mouse to highlight the file to delete and then reach  out to the delete key.
I haven't looked for a way to restore an actual Delete function.

Sorry, may be I didn't explain clearly. I really don't care about what they do with trash as I never use it. 

/rant

The trash is a stupid desgin and I always hated it in Windows. If I delete I want to delete, not to move to some hidden folder quietly taking up space.

 I don't know whether this is a Fedora bug or another brilliant gnome  upstream design choice. If it is the latter I hope it would be restored  in Ubuntu's patched version of nautilus in 15.10 and 16.04. Hopefully unity 8 will be free of gnome. It is too much to leave key components of Unity to the gnome devs.

rant/

---

### Post by buzzingrobot on 2015-06-03
It's not a bug.  I think Nemo has the delete option.  It can replace Nautilus, I hear.

---

