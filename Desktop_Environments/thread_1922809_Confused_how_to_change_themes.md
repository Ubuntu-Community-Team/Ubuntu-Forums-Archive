---
title: "Confused how to change themes"
date: 2012-02-09
forum: Desktop Environments
---

### Post by thenovelist on 2012-02-09
I am not a lover of the themes that are supplied and have been looking for some others.  I have Ubuntu 11.10 64bit.  I have down loaded the advance settings application, but can't see how you introduce a new theme.  I downloaded a theme to Home/Tony/ and then created a new .theme folder.  As from there I am at a lose as to where to go to next??  Thanks for looking hope you can help

---

### Post by Dennis N on 2012-02-09
Be sure the theme you downloaded is a GTK-3 theme.
Double click on the archive, then Extract the theme folder from the archive into ~/.themes
Start advanced settings tool.
Go to Theme tab, and set the theme in two places: Window theme and GTK+ theme.
The settings should take effect immediately.

---

### Post by thenovelist on 2012-02-09
Thanks for your reply.  I seem to have problems finding the right folder.  I did make one in HOME for themes but it has not recognised it.  So of course the advance system application isn't seeing the new downloaded theme.  Thank you once again

---

### Post by Dennis N on 2012-02-09
> **thenovelist said:**
> Thanks for your reply.  I seem to have problems finding the right folder.  I did make one in HOME for themes but it has not recognised it.  So of course the advance system application isn't seeing the new downloaded theme.  Thank you once again

.themes is a hidden folder. /home/user-name/.themes is not the same as /home/user-name/themes. The former (.themes) is probably already there created by default, but it takes an extra step to make it visible (see below).

Double click on the downloaded archive,
Hit the Extract Button (or Archive > Extract),
In the dialog that pops up, navigate to your home folder, then press Ctrl+H to display the hidden folders.
Select .themes, double click to open it, then hit Extract at the bottom.

You should be set to go.

---

### Post by Frogs Hair on 2012-02-09
The .themes and .icons folders are not in the home folder by default on 11.10 and need to be created . The usr/share/themes and icons are already present in the file system though . Make sure the downloaded packages are fully extracted by opening the theme folder . 

Sometimes there is more than one tar.gz included with a theme and if they are not extracted the theme will not appear in advanced settings .

---

