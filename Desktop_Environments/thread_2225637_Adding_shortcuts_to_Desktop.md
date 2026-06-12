---
title: "Adding shortcuts to Desktop"
date: 2014-05-22
forum: Desktop Environments
---

### Post by ccrickets03 on 2014-05-22
I am trying to add different shortcuts (or is it call launchers?) , such as Tux Paint,  on my child's desktop, but it keeps showing: Error while copying.There was an error getting information about "/" The specified location is not supported. How can I fix this?

I have Ubuntu 14.04 LTS. My child's ubuntu user account is standard.

---

### Post by slickymaster on 2014-05-22
Hi ccrickets03, welcome to the forums.

Right click the file you want a link to in your file manager, select "Create link" from the context menu and move that link wherever you want it.
In the case of application launchers, they're placed in **/usr/share/applications/**. The procedure is identical.

---

### Post by ccrickets03 on 2014-05-22
Thanks.  I did what you suggested, but it won't let me create a link. It is on the  list, but not accessible at all , as if I do not have permission or something.

---

### Post by ccrickets03 on 2014-05-22
I just discovered that  I can copy and paste from /usr/share/applications/, though

---

### Post by slickymaster on 2014-05-22
Try this:```
sudo cp /usr/share/applications/application.desktop /home/username/Desktop
sudo chmod +x /home/username/Desktop/application.desktop
sudo chown username:username /home/username/Desktop/application.desktop
```

---

