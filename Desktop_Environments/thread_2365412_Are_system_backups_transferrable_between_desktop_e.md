---
title: "Are system backups transferrable between desktop environments?"
date: 2017-07-06
forum: Desktop Environments
---

### Post by cascadia_adam on 2017-07-06
Hello,

I made the switch to Ubuntu two years ago and love it. Recently discovered that you could install different desktop environments simultaneously, and installed the KDE Plasma desktop environment alongside the native Unity one.

I have what might be a dumb question, but I'm having trouble tracking an answer down and I'm still pretty new to Ubuntu. Having both desktop environments on the same computer does seem to be slowing my computer down. I'd like to just do a clean install of Kubuntu on my system, then use the backup I have from Ubuntu to restore my files.

My question is whether it's possible to use a backup made in Ubuntu with a Kubuntu installation? I suspect yes, but I wanted to check before I made the move.


Thanks!

---

### Post by CatKiller on 2017-07-06
It depends what it's a backup of. If you've backed up all the installed programs then restoring from backup will give you all the same programs, exactly as you've got now. If it's just a backup of your user settings and data, then you'll be in a Kubuntu environment with all your settings and data, which I think is what you're after.

---

### Post by travis-falkenberg on 2017-07-09
If you are comfortable with ppa use you could use "Aptik" to backup the current state of your computer. It doesn't make a physical backup of installed programs but is used to reinstall those programs on a new installation. You have the option of reinstalling only those programs you need on the new installation. It can make physical backups of various things like home directory data, user settings, fonts, icons etc and restore them to the new installation. You can include downloaded packages and programs within the backup. Lots of options and works for me. You could also use "Clonezilla" to image your drive(s) just in case!

On your new installation the first thing you would have to do is reinstall "Aptik"

---

### Post by deadflowr on 2017-07-09
If you used Ubuntu's builtin backup program then you'd need to either get to know the command line equivalent *duplicity* or install Ubuntu's backup program *deja-dup*.
deja-dup is a gnome application that is actually a graphical frontend for duplicity and as far as I know, there is no kde (Kubuntu) equivalent program.
But installing deja-dup in Kubuntu is perfectly fine, though it will bring in some gnome dependencies.

---

