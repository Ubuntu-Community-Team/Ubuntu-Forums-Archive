---
title: "Visualize partition on the desktop"
date: 2005-06-22
forum: Desktop Environments
---

### Post by billiejoex on 2005-06-22
Hi all. I'd like to have all my HDs partition visualized on the desktop.
Does it's possible? 

Thanx a lot

---

### Post by eskaypey on 2005-06-22
[QUOTE=billiejoex]Hi all. I'd like to have all my HDs partition visualized on the desktop.
Does it's possible? 

Thanx a lot[/QUOTE]
 Do you mean you want to see capacity/free space of you hard drive?
If yes have a look at GKrellM or others.

---

### Post by billiejoex on 2005-06-22
I mean that I'd like to have all the units (hard drives, cdroms etc, usb drives...) listed in a place like happens with "My computer" used in Windows system. 
It's not too much important. It's just a curiosity. :)

---

### Post by jnoreiko on 2005-06-22
There's "df -h" in terminal.
But I agree, it would be nice to have that visually.

Does a graphical wrapper for df exist?

---

### Post by frodon on 2005-06-22
Maybe gdesklet can do something for you, it's not really easy to use but you can have graphical informations (free space, link, ...) about your partitions on your desktop.
It seems fit to your need.

---

### Post by shakin on 2005-06-22
No, he wants a My Computer icon on the desktop, like the one that's in the places menu.

I'm on KDE, so this might not be correct. The Computer shortcut in places leads to computer:// in Nautilus. So, create a shortcut to  computer://.

---

### Post by shakin on 2005-06-22
Or this...

```

$ gedit ~/Desktop/My\ Computer

```

Add this to the file, then save it:
```

#!/bin/bash
nautilus computer:///

```

Make it executable:
```

$ chmod +x ~/Desktop/My\ Computer

```

Now you can click on it to see something like My Computer. There are other guides around these forums for adding different things to that menu, like new drives you've mounted in /media.

---

### Post by billiejoex on 2005-06-22
> Or this...

Code:

$ gedit ~/Desktop/My\ Computer



Add this to the file, then save it:
Code:

#!/bin/bash nautilus computer:///



Make it executable:
Code:

$ chmod +x ~/Desktop/My\ Computer



Now you can click on it to see something like My Computer. There are other guides around these forums for adding different things to that menu, like new drives you've mounted in /media.
WIth this method only cd-rom and "file system" are visualized, not the partions mounted in /etc/fstab.

---

### Post by shakin on 2005-06-22
[QUOTE=billiejoex]WIth this method only cd-rom and "file system" are visualized, not the partions mounted in /etc/fstab.[/QUOTE]

You know what? Change that computer:/// part to /media/ and you will see nearly everything you want (assuming you have everything in fstab mounted in /media). For anything that's not there, you can create a shortcut in /media to go to /, for instance.

---

