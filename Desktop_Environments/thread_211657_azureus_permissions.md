---
title: "azureus permissions"
date: 2006-07-08
forum: Desktop Environments
---

### Post by senn on 2006-07-08
hi, ive downloaded and installed azureus using automatix . when i open it it wants to download a file swt-3.2-gtk-linux-x86.zip.but i get a warning box that says "the location '/opt/azureus' isnt writable, this update willprobably fail. check permissions and retry the update." when i go to opt/azureus i car'nt alter the permissions as it says i dont own them. any ideas?. do i need this update?.

---

### Post by atoponce on 2006-07-08
How did you install it?  I went through the update without any errors or warnings.

---

### Post by facejeans on 2006-07-27
I had the same problem, i opened nautilus with root and opened the program from there

$sudo nautilus

navigate to opt/azureus, and double click the script and run fully, not in terminal.

---

### Post by TheStrandRoads on 2006-07-29
I have the same problem.  I think you need to open Azureus as root.  I tried doing what facejeans suggested, but it did not solve the problem - thank you for the suggestion though. Azureus still could not download the SWT update.

How can I open Azureus as root using terminal?

Cheers,

J.

---

### Post by TheStrandRoads on 2006-07-29
My problem has been solved....

[http://www.ubuntuforums.org/showthread.php?t=224089&highlight=azureus+root+terminal](http://www.ubuntuforums.org/showthread.php?t=224089&highlight=azureus+root+terminal)

Hope this helps!

J.

---

