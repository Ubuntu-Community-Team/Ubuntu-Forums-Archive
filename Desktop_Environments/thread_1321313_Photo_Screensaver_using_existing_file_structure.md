---
title: "Photo Screensaver using existing file structure"
date: 2009-11-09
forum: Desktop Environments
---

### Post by Frolicsome Otter on 2009-11-09
I've been looking for an answer to this for a while.  Hopefully, someone can help out as I'm still learning about linux and Ubuntu.

I have a lot of pictures organized in a directory on a separate partition on the same hard drive as the OS, Ubuntu 9.10.  I would like to have a screen saver use these photo's in their current location.  

I've tried linking the /use/share/backgrounds folder to the pictures directory, but glslideshow doesn't read the sub-directories.

I've opened F-spot and the photos have been imported probably from a previous attempt at solving this problem.  But I can't find a way to mark them as favorites based on the sub-directory.  I don't find a way to list the photos in f-spot according to their location in the sub-directory tree.  

Does anyone know a way to use photos already organized in a directory tree on a separate partition within a screen saver?  

Any suggestions would be greatly appreciated.

---

### Post by tgalati4 on 2009-11-10
The "Pictures" screensaver will randomly display your photos in /home/username/Pictures.

You can create a directory in Pictures.  Then do a manual mount of your photo partition to that directory.  Assume your photo partition is /dev/sdc3.  Something like:

cd
cd Pictures
mkdir MyPhotos
sudo mount /dev/sdc3 /home/Frolicsome/Pictures/MyPhotos

Test it using the preview button in the control panel.

---

### Post by Veovis Muad'dib on 2009-11-10
I wouldn't do the mounting thing if the the partition has other stuff.  Try a symbolic link instead.

$ ln -s /path/to/pictures/on/other/partition ~/Pictures/OtherDrive

I'm not 100% sure that'll work with the screensaver, but go ahead and try it.  At the very worst case, you'll have a link in your pictures directory to the other drive that only works in file browsers.

EDIT: I tried it, and it works.

---

### Post by Frolicsome Otter on 2009-11-10
> **Veovis Muad'dib said:**
> I wouldn't do the mounting thing if the the partition has other stuff.  Try a symbolic link instead.

$ ln -s /path/to/pictures/on/other/partition ~/Pictures/OtherDrive



I tried this and it worked.  Thank you very much.  

As it turns out linking to the /use/share/backgrounds folder that I mentioned previously had worked in the sense that glslideshow was able to access the sub-directories after I rebooted today.  I prefer way the Pictures folder option on the Screensaver displays the photos, so that's what I'm using..

Thanks for you help.

---

### Post by Veovis Muad'dib on 2009-11-11
Not a problem.  Glad to hear it worked.

---

