---
title: "Broken menus"
date: 2006-03-25
forum: Desktop Environments
---

### Post by Ramses XI on 2006-03-25
After a expert-install of Breezy, adding a few apps and running Automatix I discovered that some of the administration apps didn't launch properly (e.g. disks-admin) I had to do the following:

1. Change privileges and owner:group on some files in /usr/share/applications/  I believe Automatix was responsible to this and not the release itself. Still I thinkt Automatix rocks \\:D/ 

2. I also had to remove "gksudo" in some .desktop files to get them to launch without getting the anoying message: "The entered password is invalid". This later issue I think should be treated as a bug, but I'm not sure if it is.

Anyone else having this problem?

---

### Post by codejunkie on 2006-03-25
[QUOTE=Ramses XI]After a expert-install of Breezy, adding a few apps and running Automatix I discovered that some of the administration apps didn't launch properly (e.g. disks-admin) I had to do the following:

1. Change privileges and owner:group on some files in /usr/share/applications/  I believe Automatix was responsible to this and not the release itself. Still I thinkt Automatix rocks \\:D/ 

2. I also had to remove "gksudo" in some .desktop files to get them to launch without getting the anoying message: "The entered password is invalid". This later issue I think should be treated as a bug, but I'm not sure if it is.

Anyone else having this problem?[/QUOTE]
        automatix isn't the cause of this one. this happend because you did an expert install, if you do a normal install, ubuntu uses sudo instead of the normal root/su, that other distros use. 

        if you do an expert install the installer enables the root account instead of sudo, but the .desktop file commands dont change they still use "gksudo nameof command" 
        
        to fix the administration menu entries you have to either add your username to the sudoers file, or edit all of the admin .desktop files to use "gksu nameofcommand" instead of "gksudo nameof command" like you had to.

---

### Post by Ramses XI on 2006-03-25
Thanks for your quick reply.

[QUOTE=codejunkie]automatix isn't the cause of this one. this happend because you did an expert install, if you do a normal install, ubuntu uses sudo instead of the normal root/su, that other distros use. [/QUOTE]

Automatix did set the rights to 700 and owner:user to "Automatix" on some .desktop files. That caused the menu editor to fail on start up.

[QUOTE=codejunkie]        if you do an expert install the installer enables the root account instead of sudo, but the .desktop file commands dont change they still use "gksudo nameof command" [/QUOTE]

I see, thanks. But this is no good because there are a lot of occasions one needs to do an expert install without the need to edit the .desktop files.

        
[QUOTE=codejunkie]      to fix the administration menu entries you have to either add your username to the sudoers file, or edit all of the admin .desktop files to use "gksu nameofcommand" instead of "gksudo nameof command" like you had to.[/QUOTE]

This is not true. My account was in the sudoers file. You have to remove gksudo and cannot use gksu instead. The later returns the same error.

[COLOR="Red"]This is now reported as a bug[/COLOR]

---

