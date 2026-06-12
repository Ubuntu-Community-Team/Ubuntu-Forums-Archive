---
title: "Menu (applications) entry duplicates"
date: 2017-11-17
forum: Desktop Environments
---

### Post by forneus2 on 2017-11-17
Hi

My main menu button opens the categories of apps with some duplicates. For example, I have Web cam Viewer both under Graphics and Sound&Video, Document Viewer both under Office and Graphics. I installed Menulibre and tried to tweak the entries list, but when I turn off the app in one category it also disappears in the other.

Not really a big issue but still I would like to have my menu more organized and categorized properly.

Any solution?

I'm using Lubuntu 14.04

---

### Post by vasa1 on 2017-11-17
Please note that Lubuntu 14.04 is no longer supported. [s]While programs will still work, you won't receive security updates and that isn't a good thing!

[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)[/s]

---

### Post by forneus2 on 2017-11-17
> **vasa1 said:**
> Please note that Lubuntu 14.04 is no longer supported. While programs will still work, you won't receive security updates and that isn't a good thing!

[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)

Sorry, I didn't quite specify. Mine is 14.04.1 and the support is until 2019.

---

### Post by vasa1 on 2017-11-17
That applies for _U_buntu but not for most of the official flavors such as Lubuntu which are supported only for three years. The link I provided is for Ubuntu and I shouldn't have provided it because it deals only with Ubuntu :(

This is the appropriate link: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS) and since the parent (Ubuntu) **is supported until 2019**, you may get security updates. Sorry for the confusion!

---

### Post by forneus2 on 2017-11-18
> **vasa1 said:**
> That applies for _U_buntu but not for most of the official flavors such as Lubuntu which are supported only for three years. The link I provided is for Ubuntu and I shouldn't have provided it because it deals only with Ubuntu :(

This is the appropriate link: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS) and since the parent (Ubuntu) **is supported until 2019**, you may get security updates. Sorry for the confusion!

Well, I'm good so far and the updates are coming. Anyway, can this issue with the menu (and libremenu) be solved? Again, it is not critical and I'm ready to just ignore it but... It's still better to be part of the solution than part of the problem ;)

---

### Post by vasa1 on 2017-11-18
Just an idea:
Copy a few of the .desktop files (of those applications which appear in more than one place) from */usr/share/applications* to *~/.local/share/applications*

Then look at the contents of a .desktop file using a plain text editor. In particular, look at the line beginning with *Categories*.

For example, in
```
[Desktop Entry]
Name=Gcolor2
GenericName=Gcolor2
Comment=Simple GTK2 color selector and picker
Exec=gcolor2
Icon=/usr/share/pixmaps/gcolor2/gcolor2.xpm
Terminal=false
Type=Application
**Categories=Application;Graphics;**
```gcolor2 will be classified under both "Application" and "Graphics".

As a test, delete *Graphics* (leaving the trailing ";" in place). Save the file (as a text file), close it. And now, gcolor2 shouldn't be seen under "Graphics" in your menu. There should be no need to log out or reboot.

The advantage of working with .desktop files copied over from */usr/share/applications* is that you have the "original" intact but the version you've created in *~/.local/share/applications* will be the one in effect.

---

### Post by forneus2 on 2017-11-18
> **vasa1 said:**
> Just an idea:
Copy a few of the .desktop files (of those applications which appear in more than one place) from */usr/share/applications* to *~/.local/share/applications*

Then look at the contents of a .desktop file using a plain text editor. In particular, look at the line beginning with *Categories*.

For example, in
```
[Desktop Entry]
Name=Gcolor2
GenericName=Gcolor2
Comment=Simple GTK2 color selector and picker
Exec=gcolor2
Icon=/usr/share/pixmaps/gcolor2/gcolor2.xpm
Terminal=false
Type=Application
**Categories=Application;Graphics;**
```gcolor2 will be classified under both "Application" and "Graphics".

As a test, delete *Graphics* (leaving the trailing ";" in place). Save the file (as a text file), close it. And now, gcolor2 shouldn't be seen under "Graphics" in your menu. There should be no need to log out or reboot.

The advantage of working with .desktop files copied over from */usr/share/applications* is that you have the "original" intact but the version you've created in *~/.local/share/applications* will be the one in effect.

Thanks for the reply. This option you are suggesting is available in menulibre under each entry - deleting categories displayed  - I had the same idea and tried to delete the irrelevant categories, but they still returned back upon the next menulibre start.. Do you think editing .desktop file directly would have a permanent effect?

I am also considering trying alacarte instead. I like menulibre more and it has better reviews from the community, but maybe alacarte editor can do what menulibre cannot? Is it ok to have these two installed at the same time?

---

### Post by vasa1 on 2017-11-18
I don't know. I don't use either. They aren't present in a default Lubuntu.

---

### Post by ajgreeny on 2017-11-18
Yes, you can have both menulibre and alacarte installed with no conflicts, as I have done in the past.

I got very used to using alacarte years ago before I knew about menulibre and I used to find it simpler and easier to work with, but times change and I think either I have got more used to menulibre or it is simpler now than it was as that is what I use now if I need to.

---

### Post by forneus2 on 2017-11-23
I upgraded to 16.04 and ran menulibre edit again. It worked fine. Seems that a newer Lubuntu version's menu is more responsive to editors. I guess the issue can be considered solved. Thanks everyone.

---

