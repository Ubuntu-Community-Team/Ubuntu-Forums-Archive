---
title: "OppenOffice in KDE"
date: 2006-03-29
forum: Desktop Environments
---

### Post by GoodPanos on 2006-03-29
I just recently installed the KDE interface (Kubuntu) and under Office I don't see the OpenOffice applications that are under Ubuntu.

Is there a way to add the OpenOffice apps on the KDE menus?

---

### Post by WolfJay_83 on 2006-03-29
They should be there if you installed the metapackage "kubuntu-desktop."
If you simply installed kde orrigionally, try opening a terminal and enter
```
sudo apt-get install kubuntu-desktop
```

That will properly configure kubuntu.

---

### Post by GoodPanos on 2006-03-29
Well, what I did is do that ```
sudo apt-get install kubuntu-desktop
``` and then I ran a script that I found here in the forums to remove all Gnome menus from KDE and visa versa.  I didn't realize that it would remove the OpenOffice menus.  Is there a way to get them back?

---

### Post by jamboarder on 2006-03-29
If the script is what I think it is, go to /usr/share/applications and find the ooo2*.desktop files.  Open each file in a text editor and remove the "OnlyShownIn=GNOME;" lines.  Do the same for any other app you want to make available in KDE (eg. GIMP, Firefox, etc.).

Hope this helps

Note:  You likely will not have permission to edit these files so you will have to use something like "kdesu kedit" or "sudo gedit" to change them.

---

### Post by GoodPanos on 2006-03-30
Thank you very much that worked great.

---

