---
title: "Scorched3D v4.0"
date: 2006-09-10
forum: Gaming &amp; Leisure
---

### Post by TheForkOfJustice on 2006-09-10
Scorched3D version 4.0 has been out for a month. When is v3.91 that is currently in the repository being replaced?

Without the newest version you can't play so we need some lovely individual to update the deb in the repos.

[http://www.scorched3d.co.uk/downloads.php](http://www.scorched3d.co.uk/downloads.php)

I installed the deb but I get an error once I finish playing that says it shut down unexpectantly and wants to put on the failsafe settings (to which I refuse because my settings are fine). I can play it with no problems at all but I just get that one error window when I exit the program. 

Annoying, but not REALLY anything to worry about.

---

### Post by jdunn on 2006-09-10
I also tried the deb package from [www.scorched3d.co.uk/downloads.php](www.scorched3d.co.uk/downloads.php).  I had to download some lib package from the repositories to get it working but, the game would always show an error in a dialog box on exit (just as 3.91 from the repositories did for me).

What finally worked perfectly for me was to:  install the alien package converter from the repositories.  Then download the scorched3d rpm from [www.scorched3d.co.uk/downloads.php](www.scorched3d.co.uk/downloads.php).  Use alien to convert the rpm to a deb package.  Install the deb package.  

The game files from the converted deb package will be installed here: 

/usr/bin/scorched3d /usr/bin/X11/scorched3d /usr/share/scorched3d

Here's the thread I started and the solution

[http://www.scorched3d.co.uk/phpBB2/viewtopic.php?t=3433&highlight=error+exit](http://www.scorched3d.co.uk/phpBB2/viewtopic.php?t=3433&highlight=error+exit)

---

### Post by HAARP on 2006-09-11
The deb always gave me segfaults. I too tried the alien solution some days ago, and now it works flawlessly. Don't use the deb!

---

### Post by glotz on 2006-09-11
You guys surely contacted the author about your discovery? Or is this some Ubuntu issue? I wouldn't know...

---

### Post by TheForkOfJustice on 2006-09-11
Yes! No more popup-thingy!

Now, does anyone want to get it into the repository? I'm too n00b to figure out how. I've just begun to learn about chrooting and deb-packaging and I'm not very confident.

---

### Post by TheForkOfJustice on 2006-09-11
> **glotz said:**
> You guys surely contacted the author about your discovery? Or is this some Ubuntu issue? I wouldn't know...

Me neither. But like I said, SOMEONE better update the repos. I would but I'm not sure how.

And on top of that, the deb I made from using alien has strict user permissions (has a lock on the top corner of the icon). Only root can access it and I have no clue how to change permissions to an 'everyone-has-access' deb.

---

### Post by jdunn on 2006-09-11
Hmm...I'm not sure how you used alien and how you installed the converted deb package.  I used the command-line and had no problems.  Using the command-line, you can easily run any command as root using 'sudo'.  You can also open a root terminal with 'sudo -i'.  So you could have done something like this:

(this worked for me and allows me to play the game as any user)
sudo alien scorched3d-4.0.rpm
sudo dpkg -i scorched3d-4.0.deb  

If you want to remove the package:
sudo apt-get remove scorched    

Sorry, I don't know how to submit packages to the official ubuntu repositories.  I would guess there's a special procedure for it.

> **TheForkOfJustice said:**
> Me neither. But like I said, SOMEONE better update the repos. I would but I'm not sure how.

And on top of that, the deb I made from using alien has strict user permissions (has a lock on the top corner of the icon). Only root can access it and I have no clue how to change permissions to an 'everyone-has-access' deb.

---

### Post by TheForkOfJustice on 2006-09-11
> **jdunn said:**
> 
(this worked for me and allows me to play the game as any user)
sudo alien scorched3d-4.0.rpm
sudo dpkg -i scorched3d-4.0.deb 

sudo alien **-d** scorched3d-4.0.rpm

That's how I made the deb and it had that little lock icon on it.

I installed it using the alien command (because I thought it was best if I installed it from the program that made it to be safe).

sudo alien -i scorched3d_4.0_2.deb

...or something like that. the '2' may have been absent. Can't remember.

And to submit something for the repos you have to get a Launchpad account, a GPG key (use seamonkey) and assemble the deb in a chroot environment. 

[https://launchpad.net/](https://launchpad.net/)
[https://wiki.ubuntu.com/MOTU/Packages/REVU](https://wiki.ubuntu.com/MOTU/Packages/REVU)
[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)
[http://wiki.freegeek.org/index.php/Basic_Debian_Packaging](http://wiki.freegeek.org/index.php/Basic_Debian_Packaging)
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

Everyone fiddling with Ubuntu should be familiar with Launchpad, chroot, GPG key-making and deb packaging. VERY useful and it will allow you to do something except complain when something is amiss in the repos.

Just one of the reasons why I'm learning about it.

---

