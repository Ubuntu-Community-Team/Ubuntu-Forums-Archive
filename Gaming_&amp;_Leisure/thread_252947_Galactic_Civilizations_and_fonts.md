---
title: "Galactic Civilizations and fonts"
date: 2006-09-07
forum: Gaming &amp; Leisure
---

### Post by jbumgar on 2006-09-07
Maybe this is the wrong place for this thread but here goes.

I installed GC2 but at the end of the install it said I needed some MS Fonts to play the game.
 
How do I go about getting those fonts on my Ubuntu?  A step by step would be nice sense I'm a noobie.

---

### Post by fatsheep on 2006-09-07
Just go to System > Administration > Synaptic Package Manager

and install the  *msttcorefonts* package.

---

### Post by fatsheep on 2006-09-07
Ok sorry for the incomplete instructions.  Here's a more complete guide:

[FONT="Verdana"]**1.**  Enable the universe and multiverse repositories.
**2.**  Go to a terminal and enter this command:
[I]
sudo apt-get install msttcorefonts[/I]

The Microsoft fonts are now installed, now we want to configure them so larger fonts will be anti-aliased just like on windows:

**1.**  Download the XML Files:
[http://www.auriance.com/docs/fonts/fontconfig.tbz](http://www.auriance.com/docs/fonts/fontconfig.tbz)

**2.**  Open up a terminal and go to the directory that you downloaded the file to.  For me this is the desktop so I am going to enter this command:

*cd ~/Desktop*

**3.**  Now we are going to extract the files to /etc/fonts with this command:

*sudo tar xvjpf fontconfig.tbz -C /etc/fonts/  *

**4.**  Log out (ctrl + alt + backspace) and log back in and take a look at a website, you'll notice a difference.[/FONT]

---

### Post by jbumgar on 2006-09-08
Ok I tried what you said but I got this messge.

jim@jim-desktop:~$ sudo apt-get install msttcorefonts
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What should I have used for the root password?

---

### Post by holbech on 2007-10-10
> Ok I tried what you said but I got this messge.

jim@jim-desktop:~$ sudo apt-get install msttcorefonts
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What should I have used for the root password?

Know this is an old post, just for completness' sake:

It means that another process is "locking" the package manager. You've probably got synaptic open. Close it and rund the command again.

---

