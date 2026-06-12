---
title: "No Koffice entries in the Applications Menu"
date: 2006-06-03
forum: Desktop Environments
---

### Post by darrensnospam on 2006-06-03
Fresh install of Dapper. 
Just installed Koffice using Synaptic.
The only entry showing up in the office menu is Kivio.
If I do a search for kspread for example, I don't see an application, but I do see:

```
/usr/share/icons/HighContrastLargePrint/48x48/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/LowContrastLargePrint/48x48/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/Tango/16x16/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/Tango/22x22/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/Tango/24x24/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/Tango/scalable/mimetypes/gnome-mime-application-x-kspread.svg
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-kspread.png
/usr/share/icons/crystalsvg/22x22/mimetypes/kspread_ksp.png
/usr/share/icons/crystalsvg/16x16/mimetypes/kspread_ksp.png
/usr/share/icons/crystalsvg/32x32/mimetypes/kspread_ksp.png
/usr/share/icons/crystalsvg/48x48/mimetypes/kspread_ksp.png
/usr/share/icons/crystalsvg/64x64/mimetypes/kspread_ksp.png
/usr/share/mime/application/x-kspread-crypt.xml
/usr/share/mime/application/x-kspread.xml
/usr/share/mimelnk/application/x-kspread.desktop
```

I'm guessing that the symlinks launch a helper application that launches Kspread.

I had this problem in Breezy. When I booted in KDE, the applicaions showed up in the menu.

Can anyone tell me why the icons don't show up in the menu in Gnome when I do a standard install from the repository? And how can I put them in my Gnome menu?

Thanks in advance.

- darrensnospam

---

### Post by darrensnospam on 2006-06-03
Update:
Allthough Kspread didn't show up when I searched the file sysem, surfing around the file sysem I found all my Icons for Koffice in the /usr/share/applink/Office directory. Clicking on the Kspread icon resuled in Kspread launching.

If anyone's interested in explaining why they didn' show up in the menu, and why it didn't show up when I used the search for files option, I'd be interested in knowing.

Perhaps this will help someone in the future.

- darrensnospam

---

### Post by epalissad on 2006-10-23
1. Go to Applications --> Accessories --> Alacarte Menu Editor
2. File --> New entry
3. Enter:
[LIST]
[*]Name
[*]Comment (optional)
[*]kspread %u (if you want to add kspread, kword etc...)
[/LIST]
4. Select icon.
5. Close.
6. Drag and drop the item you created to desired category.

Now the application you added should be in the meny.
Hope this helped.

---

### Post by epalissad on 2006-10-23
Didn't read your question completely. Honestly I don't know why they don't show up and it seems like you know enough to be able to come up with the solution I just typed. Anyway, my answer might help someone. ](*,)

---

### Post by marianom on 2006-10-23
Hi darrensnospam,
did you run updatedb after installing koffice?

---

