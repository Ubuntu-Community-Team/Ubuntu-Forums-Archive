---
title: "geeqie plugins - make quiet"
date: 2021-03-12
forum: Desktop Environments
---

### Post by holiday2 on 2021-03-12
I have a geeqie plugin defined through a desktop file (below). When I trigger the plugin, the plugin raises a dialog. I don't need that confirmation. 

In the desktop entry below I have tried setting  X-Geeqie-Verbose=false but the dialog still pops up.



```
[Desktop Entry]
Version=1.0
Type=Application
Name=Move to Archive
Categories=Graphics
Categories=X-Geeqie
Show in menu "Edit"
X-Geeqie-Menu-Path=EditMenu


# It can be made verbose
X-Geeqie-Verbose=false


#MimeType=application/x-ufraw;image/x-dcraw;


#Icon=ufraw


Exec=mv %f /home/holiday/archive

```

---

### Post by norobro on 2021-03-12
```
Exec=mv %f /home/holiday/archive
```Don't use geeqie but if you used that command on the command line it would move a file to the /home/holiday directory and rename it archive. So each time it is executed it would overwrite the file.

Are you missing a slash? 

What does your dialog say?

---

### Post by holiday2 on 2021-03-12
> **norobro said:**
> ```
Exec=mv %f /home/holiday/archive
```Don't use geeqie but if you used that command on the command line it would move a file to the /home/holiday directory and rename it archive. So each time it is executed it would overwrite the file.

Are you missing a slash? 

What does your dialog say?

Ah yes. Thanks for pointing that out but oddly enough the file is moved to the archive directory. Perhaps when the system knows it is a directory....?

The dialog displays the output of the exec. I have tried redirecting output to /dev/null  but  the dialog still pops up.

---

### Post by norobro on 2021-03-12
You're correct. If the directory exists mv will move the file to the dir.

I installed geeqie and copied your desktop file. I changed the destination directory and had to comment out the following line to get the plugin to show up in the menu:```
#show in menu "Edit"
```Worked fine with no popup dialog. I'm on Ubuntu 20.04 with geegie 1.5.1

Try  starting geegie from the command prompt and see if there are any warnings/errors.

---

