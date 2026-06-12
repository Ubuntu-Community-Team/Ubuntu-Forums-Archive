---
title: "Xubuntu 12.04 Recent Document"
date: 2012-08-22
forum: Desktop Environments
---

### Post by buster2209 on 2012-08-22
On the XFCE4 panel, there is a applet called 'Places'.  Clicking on it shows a list of drives and folders and recent documents viewed.  If I right click on the applet, I can select properties and untick 'Show recent documents' however, when I restart my machine, the recent documents are back.

I am assuming this is a bug and my work around would be to change the permissions of the text file that contains the list of recent documents I have viewed.  My only problem is I don't know what this file is called... can someone help me out?

---

### Post by brainwash on 2012-08-23
> **buster2209 said:**
> My only problem is I don't know what this file is called... can someone help me out?
I guess your are looking for this file:
```
/home/<user>/.local/share/recently-used.xbel
```

---

### Post by buster2209 on 2012-08-29
> **brainwash said:**
> I guess your are looking for this file:
```
/home/<user>/.local/share/recently-used.xbel
```

Thanks, that worked!

---

### Post by arsenic23 on 2012-09-01
This was incredibly helpful.  I have been uninstalling and crippling stupid things like this and zeitgeist from my install all week.
I just gave this file to root, and I'm good now.

EDIT:
After reboot it returned to being owned by my user.  What process even updates this file?

EDIT:
This will stop it from updating ([COLOR="Silver"]assuming your home folder is on an ext partition[/COLOR]):
```
sudo chattr +i ~/.local/share/recently-used.xbel
```

---

### Post by buster2209 on 2012-09-04
> **arsenic23 said:**
> This was incredibly helpful.  I have been uninstalling and crippling stupid things like this and zeitgeist from my install all week.
I just gave this file to root, and I'm good now.

EDIT:
After reboot it returned to being owned by my user.  What process even updates this file?

EDIT:
This will stop it from updating ([COLOR="Silver"]assuming your home folder is on an ext partition[/COLOR]):
```
sudo chattr +i ~/.local/share/recently-used.xbel
```

I did it easier than that.  I deleted the file called 'recently-used.xbel' and created a folder *in the same directory* called 'recently-used.xbel'.  Now when the computer tries to log a recently opened document, it is unable to create the file as a folder with that name already exists.

---

