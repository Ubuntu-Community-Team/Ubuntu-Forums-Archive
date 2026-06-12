---
title: "How to find a file in Wine?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by mjpatey on 2006-09-05
Hello,

I've installed a program under wine, and it seems to have gone through the install process just fine... I know it installed to Wine's "C:\\Program Files" directory.

But I searched the Wine site, and couldn't find anywhere that tells how to bring up the Wine "File Manager" (Windows-like folder tree interface) so I can find and run the file.

Anybody know how to bring up the Wine file manager?

Thank you!

-Mark

---

### Post by Anonii on 2006-09-05
Why dont you use Nautilus or the console?
Your C drive in Windows, will always be at  *~/.wine/drive_c *on Linux.

---

### Post by mjpatey on 2006-09-05
Not sure what Nautilus is... as far as the console, I assume that's the same as a Terminal?  I'll try navigating Wine's file system using the Terminal, now that I know where to look.  Thanks for the info!

I know I've seen a Wine file manager / directory tree GUI at some point, so I know it exists.  As I prefer to use a GUI if I can, does anybody know how to call that up?

Thanks!

---

### Post by Anonii on 2006-09-05
> **mjpatey said:**
> Not sure what Nautilus is... as far as the console, I assume that's the same as a Terminal?  I'll try navigating Wine's file system using the Terminal, now that I know where to look.  Thanks for the info!

I know I've seen a Wine file manager / directory tree GUI at some point, so I know it exists.  As I prefer to use a GUI if I can, does anybody know how to call that up?

Thanks!
Nautilus is your file browser if you are using GNOME, and you can call it by "ALT+F2" -> nautilus,

If you are using KDE, your file browser is Konqueror, and you can call it by "ALT+F2" -> konqueror

---

### Post by mjpatey on 2006-09-05
Anonii-

I tried to navigate to the directory you specified, but after searching the file system, the only Wine directories that exist seem to be in my Picasa folder.

I think something's wrong with my installation of Wine... time to uninstall and reinstall!  I'll post back when I have this figured out.  Thanks!

---

### Post by padre999 on 2006-09-05
> **mjpatey said:**
> Anonii-

I tried to navigate to the directory you specified, but after searching the file system, the only Wine directories that exist seem to be in my Picasa folder.

I think something's wrong with my installation of Wine... time to uninstall and reinstall!  I'll post back when I have this figured out.  Thanks!

the/.wine folder is a hidden folder. So when you started nautilus you have to make hidden files and folders visible. You can do this by pressing Strg+H. Then you should see the /.wine folder in your home directory.

---

