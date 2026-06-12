---
title: "How to register an application in the system ?"
date: 2016-06-24
forum: Desktop Environments
---

### Post by jrrpnani on 2016-06-24
Hello: 

I'm using Ubuntu Gnome 16.04 x64 bits, and I have a problem with Gnome-font-viewer. The application it's not the default app to open font type files. I have tried to associate it in Nautilus, at proprieties "open with ...", but gnome-font-viewer it's not in the list. Searching in the Internet  I found how to associate the extensions with mime-types, using Ubuntu Tweak.
But my question is  **how can I register gnome-font-viewer with the system** again? I have removed and reinstalled the gnome-font-viewer, but without success.

---

### Post by vasa1 on 2016-06-24
Can you locate the .desktop file for gnome-font-viewer? It should be in **/usr/share/applications**. Copy that file over to **~/.local/share/applications** without using sudo.

Then look for the line starting with **Exec=**. Does it end with **%f**? If it doesn't, just add that at the very end of the Exec= line. In other words, add a simple space followed by **%f**.

Now see if Nautilus offers gnome-font-viewer as an option in Open With ....

(Idea from [https://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/](https://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/))

If it doesn't, no big deal. You still have your original .desktop file in /usr/share/applications.

BTW, I think in technical terms, anything installed using dpkg (and that means via the software center or apt or apt-get or gdebi) is registered with the system automatically. There's nothing further that needs to be done.

---

### Post by jrrpnani on 2016-06-24
I've followed your indications and it's work.
I have found a problem at the .desktop file of the gnome-font-viewer. The original file in /usr/share/applications copy to my ~/.local/share/applications doesn't work. I have created a second entry at the menu editor called Font Viewer. Then I edit it from /.local/share/applications and I've copy the missing parameters. The line with Exec= finished with %u. I changed it with %f. After that I have two files for the Font Viewer, one works (the one I've created) and other doesn't (i'm not sure why). As a curiosity after that the font viewer appears in the list of applications to be used in "open with..." in Nautilus.
Thank you very much.

---

