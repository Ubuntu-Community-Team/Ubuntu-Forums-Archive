---
title: "how to change icons for particular file extensions (not for a particular file)"
date: 2005-05-02
forum: Desktop Environments
---

### Post by iomicifikko on 2005-05-02
id like to change icons for a few extensions but there is not such an option in theme manager (i can just set icons style in general) and if u right-click on file properties u can change icon for that particular file, not for the extension,  any idea?


thanks all, bye

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=iomicifikko]id like to change icons for a few extensions but there is not such an option in theme manager (i can just set icons style in general) and if u right-click on file properties u can change icon for that particular file, not for the extension,  any idea?


thanks all, bye[/QUOTE]
 This can only be done by changing the Icon theme you are using. A quick-and-dirty way is to manually edit the theme you are currently using: 

 Assuming you use Gnome, check which icon theme you are using (in Preferences->Theme->Theme details->Icons). Now go to 
/usr/share/icons/<themename> /48x48/mimetypes/
and manually replace the png files you want (using sudo). For example, icon for html files (mime type text/html) is defined by the file gnome-mime-text-html.png

If you use icons of sizes other than 48x48 (this depends on your screen resolution, magnification set in Nautilus, etc), then you might need to do it for other sizes, too.

---

### Post by ow50 on 2005-05-02
And the long-and-elegant way would be to create a new icon theme in ~/.icons and have that theme inherit the theme you're currently using. Easiest would be to download an icon theme or copy from /usr/share/icons and edit the icons, directories and the index.theme file.

---

### Post by iomicifikko on 2005-05-03
yeah, i discovered all this giving a look in synaptic at all the files installed by the related packages, sigh.

anyway thanks for answering.  bye!

---

