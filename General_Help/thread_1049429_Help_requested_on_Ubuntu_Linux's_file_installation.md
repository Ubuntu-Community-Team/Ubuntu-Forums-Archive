---
title: "Help requested on Ubuntu Linux's file installation method"
date: 2009-01-24
forum: General Help
---

### Post by Brendo613 on 2009-01-24
I would like help understanding where a program is installed to.  I found [ a website](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html) which explains the Ubuntu filesystem heirarchy, but doesn't clarify everything for me. 

For example, I'd been using a program - soundKonverter - and wanted to restore the default settings, which I attempted doing by (in Synaptic) completely removing the program, and then searching for anything mentioning soundKonverter and deleting those remaining files, too, but to no avail.  When I reinstalled soundKonverter, my same previous settings were there, not the defaults I was aiming for! This tells me that my configuration files were kept somewhere on the computer.  

Where, then, are these files located?  I've never successfully uninstalled any program to completion, in such a way that upon reinstall, the defaults were resumed.  I'd greatly appreciate knowing where to look for the default config files.  Thanks, -Brendan

---

### Post by oldos2er on 2009-01-24
Your config files are in your /home/username directory. Open Nautilus, hit Ctrl-H, and you will see all the hidden files (beginning with a .). In Synaptic, if you choose 'completely remove' your config files should be deleted along with the program files (this is the GUI equivalent of the command 'apt-get --purge).

---

### Post by yeats on 2009-01-24
You will also find many config files in the /etc directory - FYI.

---

### Post by Yashiro on 2009-01-24
If you run the app on your account and don't use sudo to run it, chances are that any changes you make do not modify any global defaults. The changes are *usually* tied to your user folder/account.

**sudo apt-get purge <theapp>** in a terminal might work too. This attempts to purge the files while in superuser mode.

Or look in your home folder using Nautilus (the gui file browser).
Press Ctrl+H. Ctrl+H reveals hidden files. 
Check for and remove folder/files related to the app. Possibly called .soundkonverter, .config/soundkonverter etc.

---

### Post by Brendo613 on 2009-01-26
No luck finding any config files for soundKonverter.  It's not just this program that I want to restore to default, it's also Audacity, as well as ALSA in general.  Problem is, I don't want to reinstall the whole system, because I'll lose my wireless card configuration, as well as all personal settings.  Thank you for the suggestions; maybe what I'm trying to do isn't possible?  

With ALSA, in the past, I had to modify some configuration files because my USB mixer stopped being recognized by the computer, for whatever reason.  ALSA hasn't been right since, but upon a reinstall, I haven't had anything changed.  

This is one thing I understood how to do in Windows that I don't in Linux.  Remember c:/Program Files/*whatever program* ?  You could just remove that!  :D  

Any more pointers where configuration files are laid out?  Maybe there's a way to read the program's installer to see where it places files?

---

### Post by Yashiro on 2009-01-26
Unless you run programs using sudo the config files, 99% of the time, have to be in your /home folder.

If you messed about with stuff as super user, then the files can be anywhere. Usually in /etc /usr or /var.

Why not open the program, change some options, close it. Then search for files modified in the last minute. Job done.

---

### Post by Brendo613 on 2009-01-26
Found out why I couldn't find those config files you three were mentioning ... by going to places, then search for files, I was exempting hidden files ... duh!  I did "locate soundKonverter" in console, and then the same thing for Audacity, and was able to have stock program defaults restored!  Thanks for the pointers.  I still am having issues with Audacity, but that's a complete separate issue.  

Now I'm going to attempt restoring ALSA's defaults ... I'll be back with questions, most likely.  Thanks for your help so far, everyone

---

### Post by estyles on 2009-01-26
I guess you already figured it out, but it's worth noting that while most programs keep their config files at /home/username/.appname, a lot of kde programs keep them at /home/username/.kde/share/apps/appname

I had that problem with amarok.  And no, I don't know why "completely remove (including config files)" doesn't actually do what it says.

---

### Post by Brendo613 on 2009-01-26
Good point; I wouldn't have found soundKonverter's config file by looking for .soundKonverter.  It was hidden in said .kde folder format.

---

