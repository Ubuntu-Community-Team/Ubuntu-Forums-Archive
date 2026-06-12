---
title: "adding a startup script."
date: 2007-09-05
forum: Desktop Environments
---

### Post by ebrammer252 on 2007-09-05
I'll be the first to admit I'm a n00b.  I've never played with any versions of Linux before but I've heard so many good things about Ubuntu I figured I'd start with Fiesty.  So I've got everything set up how I'd like it.  I'm just trying to add an automatic wallpaper changer I found on the forums, more specifically : [http://ubuntuforums.org/showthread.php?t=264672]("http://ubuntuforums.org/showthread.php?t=264672")
So I've got the change-background.sh file on my desktop I just need to know where to put it and how to make it active.  I read that it needed to be in the .bin file or the init.d file, but every time I try and cut/paste it tells me I do not have permission.  Can anyone help me learn how to obtain permission and then make the script active at startup?

Thanks a bunch,
Eric

---

### Post by banewman on 2007-09-05
The easiest way to add a program to startup is to go to system-preferences-sessions - in the menu and click new in the startup programs page. Giive it a name and then type the address to i t- e.g /home/you/desktop/background_changer.sh. You need to check that the file is executable - right click the file and scroll to properties, then click permissions - that should show if it is executable. If it is not then try to check the boxes - if that fails - go to terminal and type -sudo  chmod  a+x  /path/to/file - and that will make it executable. Hope this helps. :)

---

