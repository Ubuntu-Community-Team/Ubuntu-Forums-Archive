---
title: "Rooty toot toot"
date: 2006-01-13
forum: General Help
---

### Post by Thinminnow on 2006-01-13
Hi All,

First off I'm aware of the sudo way of doing things with Ubuntu.
Here's my pickle: I'm using an installer from Samsung for my ML-1740 laser printer. When I launch Samsung's installer program in the shell as sudo linux-config, a dialog box appears with ROOT as the user and another field for entering the pw. I've tried setting the root password in the shell with instructions I'll found here. But the dialog window that's part of the Samsung installer doesn't accept it.

Here are their instructions: 

You need to be logged in as the super-user (root) to be able to install this
package.

- Run the 'setup.sh' script on the CDROM to launch the installation program, 
  if the installer didn't start automatically upon insertion of the CDROM in
  your drive.

- You may choose either the "Recommended" or "Expert" types of installation.
  "Recommended" is fully automated and won't require any interaction on your
  part. It will install the product under /usr/local/linuxprinter.
  The "Expert" installation allows you to fine-tune these settings and choose
  where the package will be installed.

***Got to this point fine***

- Once the installation is done, you will be offered the option to start the 
  Configuration Tool, which allows to install and configure new Linux printers
  into your Linux system.

- The configuration tool can later be launched by using the 'linux-config'
  command, or through the menu item that may have been added to your Gnome / KDE
  menus.

Any help would be greatly appriciated.

Cheers,

Rich

---

### Post by hillbilly on 2006-01-13
hmm...I dont know whether this will help you  or not. But try opening the graphical installer with gksudo instead of sudo. I had read somewhere that to run graphical apps as root, gksudo should be used and not sudo. I am not sure why, though :-/

---

### Post by Aaron Hoy on 2006-01-13
I am also having problems with ubuntu's sudo way of doing things.  Have you tried activating root and then using su?  For me even this did not work, but it might in your situation.

---

### Post by astoltz on 2006-01-13
Not sure it will make a difference but try ```
sudo -s
```Enter your password when promted.  This will leave you at a root prompt.  Then try starting linux-config from there.

---

### Post by Aaron Hoy on 2006-01-13
for most purposes that would have the same effect as "su" but in my case it did not work.

---

### Post by BitTorrentBuddha on 2006-01-13
I have a similar problem, except I can't access any of the GUIs in the administration section, I'm prompted for a password but when I enter the password nothing loads :confused:

---

### Post by Thinminnow on 2006-01-13
Thanks Everyone,

Tried all of the suggestions and no cigar. I'll keep rooting around for answers. 

Now to try and get sound from BOTH speakers. Joy joy

Rich

---

### Post by aysiu on 2006-01-13
[QUOTE=Thinminnow]
When I launch Samsung's installer program in the shell as sudo linux-config, a dialog box appears with ROOT as the user and another field for entering the pw. I've tried setting the root password in the shell with instructions I'll found here. But the dialog window that's part of the Samsung installer doesn't accept it.[/QUOTE] Unless you did an expert install the "root" password the dialogue is asking for is actually your user password (assuming you're the first user you created during installation).

---

### Post by daahli on 2006-01-16
Hey,

I have the same printer and was able to get it working by temporarily enabling the root account. Check out this thread for a detailed explanation:

[http://www.ubuntuforums.org/showthread.php?t=31796](http://www.ubuntuforums.org/showthread.php?t=31796)

---

