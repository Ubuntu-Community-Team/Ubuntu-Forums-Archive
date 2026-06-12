---
title: "using the nautilus-gui for file-operations?"
date: 2009-06-20
forum: Desktop Environments
---

### Post by hachel on 2009-06-20
Hello

I wonder if it's possible to use the gui nautilus uses when copying or moving files.
Like "nautilus-copy foo to bar".
I made myself a nautilus-action to transfer files to my external harddrive with "cp {%M} to /media/USBHD", and it doesn't show any progress while copying.
I could do it via the terminal so that I at least see possible error-messages but it also doesn't show progress.
The reason I use a nautilus-action to do that is that it's such a hassle to right-click, then click send to..., then chose my external drive (because there's alway evolution preselected even though I don't use it) and then hit send. Above all there isn't no progess-bar either.

cheers

---

### Post by VCoolio on 2009-06-20
Maybe [this]("http://www.gnome-look.org/content/show.php/Watcher+--+Zenity+Progress+Window?content=104818") can help you, didn't try it myself as I would not use it enough to remember how it works. You'll need zenity of course, I don't think it comes with Ubuntu by default, but it rocks combined with home-made scripts.

---

