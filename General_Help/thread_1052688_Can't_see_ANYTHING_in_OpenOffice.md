---
title: "Can't see ANYTHING in OpenOffice"
date: 2009-01-28
forum: General Help
---

### Post by Trixilver on 2009-01-28
This is what every OpenOffice app looks like at the moment:

[[IMG]http://img89.imageshack.us/img89/8563/openofficeglitchdd0.th.png[/IMG]](http://img89.imageshack.us/img89/8563/openofficeglitchdd0.png)

As you can see, the menu buttons (e.g. File, Edit, etc) have disappeared and only flicker occasionally when I hover over them. I had the exact same problem with Wine yesterday - before I fixed it - and now I've found OpenOffice is doing the exact same thing.

Btw, this doesn't have anything to do with OpenOffice 3.0 as it was doing this before I tried upgrading to see if that would fix it, but it hasn't.

---

### Post by Yellow Pasque on 2009-01-28
It sounds like an error with the video driver or X.org. Can you give us more information on that?

---

### Post by Trixilver on 2009-01-28
Well, I've got a NVidia GeForce 6600. The driver I have installed is version 96.43.09. I installed this driver over version 177 a few days ago because the later drivers were giving me problems with fullscreen Wine apps (but I guess it's this older driver which is what's giving me this problem).

As I said before, I had this invisible text problem with Wine yesterday so I searched for a solution and ended up fixing it by changing a part of the user.reg file from
```
[Software\\Wine\\X11 Driver] 1232703649
"UseXRandR"="N"
```
to
```
[Software\\Wine\\X11 Driver] 1232703649
"ClientSideWithRender"="N"
"UseXRandR"="N"
```
and everything in Wine worked 100% again.

---

### Post by Trixilver on 2009-01-28
bump

---

### Post by ChEeZeBaLL on 2009-01-28
It's a bug with the anti aliasing which is enabled by default. To solve the problem:


Start Open Office word processor. Click on the tools menu (7th from left, 3rd from right in Oo 3.0 ) The last (bottom)option on the tools menu is options. That will open a dialog box that you won't be able to read but in the left pane just click down the options until you see "Options-OpenOffice.org-View" in the dialog title bar. At this stage you should see several check boxes in the right pane. Uncheck all of them and then click the ok button at the bottom of the dialog box. You won't be able to read it but it is the leftmost of the bottons at the bottom. The dialog should close and your menus should be readable now.

---

### Post by Trixilver on 2009-01-30
> **ChEeZeBaLL said:**
> It's a bug with the anti aliasing which is enabled by default. To solve the problem:


Start Open Office word processor. Click on the tools menu (7th from left, 3rd from right in Oo 3.0 ) The last (bottom)option on the tools menu is options. That will open a dialog box that you won't be able to read but in the left pane just click down the options until you see "Options-OpenOffice.org-View" in the dialog title bar. At this stage you should see several check boxes in the right pane. Uncheck all of them and then click the ok button at the bottom of the dialog box. You won't be able to read it but it is the leftmost of the bottons at the bottom. The dialog should close and your menus should be readable now.

Oh, wow. Thank you, you're a champ!

---

### Post by juan234 on 2009-02-10
I had the same problem with wine, openoffice and I read some where Abiword.  there seems to be a problem with the restricted driver see [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/300476](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/300476) deactivating the driver worked for me.  I can see movies better also.

---

### Post by ChEeZeBaLL on 2009-02-12
> **juan234 said:**
> I had the same problem with wine, openoffice and I read some where Abiword.  there seems to be a problem with the restricted driver see [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/300476](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/300476) deactivating the driver worked for me.  I can see movies better also.

there's an easy fix for the wine problem if you still want to use the restricted video driver.


create a text file called "settings.txt". insert the following in the text file and save:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

then in a terminal (in the folder where you put the txt file) type:
wine regedit settings.txt


that should do the trick.

---

