---
title: "Can't change icon on the unity bar"
date: 2014-09-26
forum: Desktop Environments
---

### Post by jlh68 on 2014-09-26
I have a blank icon for LibreOffice on my unity panel.  I have tried using Main Menu to change the properties of the icon to one that has the LibreOffice icon.  It will not persist.  See icon below in attachments.  This has worked o n my other computer which is using the same version of Ubuntu (14.04 LTS).

So how do I change the blank page to the LO icon?

---

### Post by CantankRus on 2014-09-27
```
cp /usr/share/applications/libreoffice-startcenter.desktop ~/.local/share/applications
```

Then..
```
gedit ~/.local/share/applications/libreoffice-startcenter.desktop
```

and change
```
Icon=libreoffice-startcenter
```

to
```
Icon=[COLOR="#A9A9A9"]<path to your image>[/COLOR]
```

---

### Post by jlh68 on 2014-10-12
I just got around to making the change.  
Thanks, your i nstructions worked just great.

---

### Post by jlh68 on 2015-06-10
New computer.  It came with Ubuntu 15.04 OS.  The paths are different than the ones in the solution below.

Need help figuring out new paths and syntax for command to change Icon.

---

### Post by CantankRus on 2015-06-10
Just used the same procedure on my 15.04 install and worked.
Check your **~/.local/share/applications/libreoffice-startcenter.desktop** file is using 
the full path to an existing image.
eg
```
Icon=**/home/glen/Pictures/icons/LibreOfficeIcon2.png**
```

---

### Post by jlh68 on 2015-06-11
Again my friend you have helped me accomplish the task.
I hunted and hunted for the file.  Got frustrated and just used the terminal and the code you gave me last time, added the new path to the Icon and what do you know,, after a reboot I had my icon on the Unity panel.  It sure beats having 4 or 5 different LO app Icons  taking up space.  I am not sure why the Ubuntu team did not set it up the way we have done it?  I guess they were thinking of the small screen use of it.

Thanks for you help.

---

### Post by jlh68 on 2016-02-05
**CantankRus**  Well I need help again. I can not get the gedit file to save with my changes.  It looks like it has saved with the changes, but when I reboot to get the icon to display, it does not display and when I check the file it has reverted to the old Icon=  stuff.

---

### Post by jlh68 on 2016-02-06
Well it seems that I cannot key the letters in correctly.  Used lower case when it should have been upper case, and so on.  I suppose that is what cataract(s) do.  Actually I now only have one cataract (left eye) and a new lens in the right eye.  I also have new cornea tissue in the right eye and I do not have correction to read with the right eye yet.  So the left has to do the reading thought the cataract.  Bottom line is that I just did not see correctly to get the icon in the unity bar.  Persistence, and I got it.

---

