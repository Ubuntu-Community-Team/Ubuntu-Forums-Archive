---
title: "right click menu within file managers, add option"
date: 2006-11-09
forum: Desktop Environments
---

### Post by dannyboy79 on 2006-11-09
I am running Xubuntu Dapper. My goal is to have an extra option when I right click within thunar, currently, if I click on a file and right click and then click on delete, it'll throw the file in my trash bin (i installed 0.4.0 Rc1 from here, [http://thunar.xfce.org/download.html](http://thunar.xfce.org/download.html)) and sometimes that not what i want, i want it to be deleted permanently. so how do i add that option so that it shows up in my right click menu? i think that if i do rm and then the location and file it'll delete the file permanently or I know I can just empty my trash, but I would like to set this up. can anyone help me? i believe I already know how to do it nautilus because there is a scripts folder that contains scripts (like if you right click on a file in nautilus, there is a script that automatix installed that can allow you to bring up nautilus to that same folder and file but you'll have root access) so I think I can just learn how that's done and copy from that, but I don't know how this would be done in xubuntu and thunar. i would really appreciate the help.

---

### Post by -Phi- on 2006-11-09
In Thunar:
Edit > Configure custom actions > Add new custom action (the + sign)

Choose an appropriate name and description (Delete Permanently) and put in a command something like```
rm %f
```
(%F will do the same for all selected files. Though you might want to figure out a script that will pop up a dialog to confirm you want to delete. In that case, put the script location in the command box). Under the Appearance Conditions tab you probably want to check all.

- Phi

---

### Post by dannyboy79 on 2007-01-04
i tried creating a script for permanently deleting files when I open nautilus to a location that normally only root can delete or whatnot. I know that automatix installed a script that will open nautilus with root privalages but I don't want this, I just want to be able to delete it stuff by right clicking, then hitting perm delete, then a box will come up and have me type in root password and ask me for sure if I want to delete this and then it will do it. can anyone help me create this script?
now arnieboy tried to help me and gave me this:

#!/bin/bash
#created by arnieboy
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "Do you have root access?"`
sudo rm $NAUTILUS_SCRIPT_SELECTED_URIS

but it doesn't work. any suggestions?

---

