---
title: "How to create link/script/? to open 2 Nautilus windows?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Cordate on 2005-11-20
Hello everyone,

I have several particular windows to directories that I often open to view files in and swap them around. I typically use 3 links on my top panel to open these. I am wondering if there if a way to create one button that will open these 2 or 3 Nautilus windows with just one push. 

I suspect a script with commands to Nautilus to open these windows is probably the way to go, but I don't know what those commands might be. Or maybe there's something simpler and more intuitive?

Thanks for your help!

-Cordate

---

### Post by 23meg on 2005-11-20
Enter the following into a blank document in gedit, with the appropriate paths```

#!/bin/bash
nautilus -n /path/to/folder1
nautilus -n /path/to/folder2
nautilus -n /path/to/folder3

```
Save it with a .sh extension and make the file executable with "chmod +x". Create a launcher that points to the script.

---

### Post by Cordate on 2005-11-22
Awesome, it works fine :)  ...and I can use this tidbit of Nautilus knowledge for more little custom commands. Thanks!

---

