---
title: "problem in installing login screens"
date: 2011-06-15
forum: Desktop Environments
---

### Post by apoorvmunshi on 2011-06-15
i installed art manager but cant install login screens through it. I have attached the screenshot . It doesnt show the install option . what to do?

---

### Post by apoorvmunshi on 2011-06-15
If i press the download only button , then is asks for the directory. After selecting the directory , nothin happens...:(

---

### Post by FormatSeize on 2011-06-15
Try this:
 
First, make your Appearance window pop up automatically when you log in. After running the following command, logout, then restart. 
```

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```
Once you are logged back in, set your Apperance properties the way you want them at the login screen.
 
Next, you have not have the Appearance window popping up every time you log in (that would be a pain). Use the following command to do that:
```

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
 
Then you are set.

---

