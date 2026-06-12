---
title: "xUbuntu 18.04 USB storage opens with thunar instead of PCManFM"
date: 2018-11-05
forum: Desktop Environments
---

### Post by Adam_GUI on 2018-11-05
I'm running xUbuntu 18.04 64bit.
In Preferred Applications, I have my File Manager set to PCManFM as my default.

However, when I insert any USB storage medium, it opens in Thunar.

Is there an extra setting somewhere that I can set to open PCManFM as expected?

---

### Post by #&amp;thj^% on 2018-11-05
Give this a shot:
```
sudo mv /usr/bin/thunar /usr/bin/thunar.bak

```
This backs up the file and renames it "thunar.bak"
Now this should replace thunar as file manager and now use PCManFM:
```
sudo ln -s /usr/bin/pcmanfm /usr/bin/thunar
```
Now see what is used opening files/USB's/Disks.
To revert back:
```
sudo mv /usr/bin/thunar.bak /usr/bin/thunar
```

---

### Post by Adam_GUI on 2018-11-05
> **1fallen said:**
> Give this a shot:
```
sudo mv /usr/bin/thunar /usr/bin/thunar.bak

```
This backs up the file and renames it "thunar.bak"
Now this should replace thunar as file manager and now use PCManFM:
```
sudo ln -s /usr/bin/pcmanfm /usr/bin/thunar
```
Now see what is used opening files/USB's/Disks.
To revert back:
```
sudo mv /usr/bin/thunar.bak /usr/bin/thunar
```

This seems to have worked.  I was prompted what to do.  I selected "Open with file manager" and it opened in PCManFM.

Thank you.

---

### Post by Adam_GUI on 2019-09-26
I don't mean to necro-bump this, but, starting around a reboot last night, 
I could not open "Properties" on the desktop dialog nor add any icons to the desktop
without a "Process org.xfce.FileManager exited with status 1" error.

This function could have been happening for longer.  I didn't notice before last night.

Restoring thunar from thunar.bak restored functionality without the error.

However, USB drives are now back to opening in Thunar by default.

Guess I just get to live with it.

---

