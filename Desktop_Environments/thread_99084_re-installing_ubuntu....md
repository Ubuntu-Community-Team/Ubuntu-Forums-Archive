---
title: "re-installing ubuntu..."
date: 2005-12-04
forum: Desktop Environments
---

### Post by yeahyeahyeah on 2005-12-04
Can I just copy (as root) my entire "/" partition to an external drive, reformat my computer, and copy the entire "/" data back? Using a live CD, of course.

Trying to figure out the best way to reformat my machine and keep all of my data, applications, and customizations.

---

### Post by aysiu on 2005-12-04
PartImage?

---

### Post by wgrant on 2005-12-04
[QUOTE=yeahyeahyeah]Can I just copy (as root) my entire "/" partition to an external drive, reformat my computer, and copy the entire "/" data back? Using a live CD, of course.

Trying to figure out the best way to reformat my machine and keep all of my data, applications, and customizations.[/QUOTE]

Erm, there is no point in reformatting your system and then copying the entire tree back, as that would restore the system identically to how it was before the format, except that it would probably be unbootable!

Backing up your home directory should get most of the data and customisations, and you can install the applications again.

William.

---

### Post by yeahyeahyeah on 2005-12-04
Well my exact issue is that Grub is giving me an error that I can't seem to fix (error 17). 

These are the things I am worried about:

  #1. All of the customizations I've done to Gnome, KDE (i.e. icons,
        drive maps, panels, wallpaper, etc)
  #2. Games I've installed (i.e. Freeciv, Battle of Wesnoth)
  #3. Applications I've installed (i.e. Gnomebaker, KDevelop)

Then I have concerns about my WINE install, and the apps I've installed under that.

And I've installed Apache.

This is my first Linux re-install.



[QUOTE=fujitsu]Erm, there is no point in reformatting your system and then copying the entire tree back, as that would restore the system identically to how it was before the format, except that it would probably be unbootable!

Backing up your home directory should get most of the data and customisations, and you can install the applications again.

William.[/QUOTE]

---

### Post by wgrant on 2005-12-04
Ahh, that is better reason for doing what you asked about. Have you asked anybody about the grub error? Is there an error message, not just a number? I am sure we can help you fix GRUB, thereby preventing you from having to reinstall Ubuntu.

William.

Edit:

I just read up on Error 17, and there are quite a number of issues that have caused it for various people. yeahyeahyeah, if you can post your system specs, as well as partition layouts etc., we can probably solve the issue.

---

### Post by yeahyeahyeah on 2005-12-05
Thanks. I actually just re-installed. I ended up needing to do so for other reasons anyway.

Before I did anything, I backed-up my /home dir. So can I just copy it back? What do I lose if I do that?

[QUOTE=fujitsu]Ahh, that is better reason for doing what you asked about. Have you asked anybody about the grub error? Is there an error message, not just a number? I am sure we can help you fix GRUB, thereby preventing you from having to reinstall Ubuntu.

William.

Edit:

I just read up on Error 17, and there are quite a number of issues that have caused it for various people. yeahyeahyeah, if you can post your system specs, as well as partition layouts etc., we can probably solve the issue.[/QUOTE]

---

