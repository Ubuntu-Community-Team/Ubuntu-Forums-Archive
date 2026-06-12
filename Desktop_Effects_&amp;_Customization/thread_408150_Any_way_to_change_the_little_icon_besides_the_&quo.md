---
title: "Any way to change the little icon besides the &quot;Applications&quot; button?"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Fireblend on 2007-04-13
Hey. I was customizing my desktop and I was wondering if there was some way to customize that little icon besides the "Application" text in the upper left corner. Also, I was wondering if I could change those buttons' font/color.

Thanks in advance!

---

### Post by yabbadabbadont on 2007-04-13
Search in /usr/share/icons (and it's subdirectories) for "distributor-logo.png"  Change it and it should change the main menu icon.  Remove it and the icon should default back to the Gnome "foot" logo.

---

### Post by Fireblend on 2007-04-13
Yay, thanks!

---

### Post by Fireblend on 2007-04-13
Sorry to keep bothering, but how do I delete/move a file with the terminal? I have to be root to handle those files and I'm not so good at the terminal...

---

### Post by Shay Stephens on 2007-04-13
try running this in the terminal
```
gksudo nautilus
```

That will open a gui file browser with root permissions to do whatever you want.  But don't keep it open longer than you need.

---

### Post by yabbadabbadont on 2007-04-13
Preface any command that needs root privelige with "sudo".
Example:```
sudo rm file-to-be-removed
```

---

### Post by Fireblend on 2007-04-13
Hmm, ok. Now it seems I can't find what file it is >_> there are about 8 icons called that in that directory you directed me to. I tried replacing the ones from 22pixels and 24 pixels directory, rebooted and it didn't change D:

---

### Post by yabbadabbadont on 2007-04-13
Did you restart gnome-panel after you moved/removed the image?  Either log out and back in or hit Alt-F2 and run "killall gnome-panel".

---

### Post by Fireblend on 2007-04-13
I actually restarted the computer.. wouldn't that have done it?

---

### Post by yabbadabbadont on 2007-04-13
Yep.

---

### Post by ustrucx on 2007-04-25
this is sad, i dont like the ubuntu colors (i like colors like green, blue) and i cant change the menu icon, i removed every ubuntu icon i found in every folder at /usr/share/icons/.
its just sad that u have to live with that in a linux box.

---

### Post by shane2peru on 2007-05-08
Someone else directed me to this link:

[http://www.ubuntuforums.org/showpost.php?p=519310&postcount=13](http://www.ubuntuforums.org/showpost.php?p=519310&postcount=13)

However, I tried this and it didn't work for me.  Does anyone else know about changing that button?  I used to have a green start button down there before I upgraded to 7.04, and now it is gone!  I want it back, now I just have a red X indicating that the icon is gone.  Help!  Thanks!

Shane

---

### Post by shane2peru on 2007-05-08
ok, never mind, I just copied the png to that directory listed here and it worked.  Although this still doesn't solve the problem, if someone wanted to change that.  It would be nice to know the sure fire way of changing that around.  Surely someone must know how to do this.

Shane

---

