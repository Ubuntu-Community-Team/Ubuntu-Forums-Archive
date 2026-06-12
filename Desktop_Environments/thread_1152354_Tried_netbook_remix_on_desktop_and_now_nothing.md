---
title: "Tried netbook remix on desktop and now nothing"
date: 2009-05-07
forum: Desktop Environments
---

### Post by rcayea on 2009-05-07
Hey folks,

For some crazy reason I tried netbook remix on my desktop. I selected desktop-switcher and immediately got a warning that something was wrong. So now I have no netbook look. then I tried to right click on the desktop and I can't seem to do that. I have lost everything that was on my desktop before this netbook try. 


any ideas how I can revert back to my standard gnome desktop?  

Also here is some info from my nvidia card when I looked at it...

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

Unknown id: Using
rcayea@randycomputer:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.


I appreciate any help.

thanks,
Randy

---

### Post by rcayea on 2009-05-08
I fixed this by physically moving the .config, .gconf, and .gnome2 files from my user folder to a random folder in my Documents folder. After I rebooted my computer came back with a fresh desktop and a lot of settings are reset to default but I didn't lose any documents/data etc. 

Does anyone know how to mark a thread as solved?

Thanks,
Randy

---

### Post by rykel on 2009-12-16
> **rcayea said:**
> I fixed this by physically moving the .config, .gconf, and .gnome2 files from my user folder to a random folder in my Documents folder. After I rebooted my computer came back with a fresh desktop and a lot of settings are reset to default but I didn't lose any documents/data etc. 

Does anyone know how to mark a thread as solved?

Thanks,
Randy

Randy,

Thanks so much for your answer!

I have been plagued with the inability to restore my desktop to default for a while now too...

I have opened a Question on Launchpad for this very purpose, hopefully a helpful dev will be able to do something abt it!  :P

[https://answers.launchpad.net/gnome-desktop/+question/94324](https://answers.launchpad.net/gnome-desktop/+question/94324)

---

