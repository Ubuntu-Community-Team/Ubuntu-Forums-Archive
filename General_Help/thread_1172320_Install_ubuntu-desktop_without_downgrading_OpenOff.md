---
title: "Install ubuntu-desktop without downgrading OpenOffice"
date: 2009-05-28
forum: General Help
---

### Post by dzcomposer on 2009-05-28
I am running Intrepid on a HP Mini 1010NR (the only distro I was able to find that detected all of the hardware). I tried to update to Jaunty, but Jaunty seems to not detect the sound hardware in this thing, so I had to downgrade.  So, after reformat, I set up all of my software. I need OpenOffice 3.x, as all of my other machines have that and I do not want file version issues. So, I uninstalled the 2.x that comes with Ubuntu and installed 3.1 debs from the OOo site.   I ran the updater to get all of the packages up-to-date.  Due to a failed update to one of it's dependencies, I ended up having to uninstall ubuntu-desktop in order to re-install the dependency. I was able to get everything else back.    I ran into an issue when reinstalling ubuntu-desktop: When I use Synaptic or apt-get, it wants to uninstall openoffice.org 3.1, which I had installed previously, and downgrade it to 2.something.    This is unacceptable. Due to configurations I have made, I would really rather not downgrade and then re-upgrade.    Even though my system seems to function fine without this package, I cannot help but think something is broken because of this, and I just haven't found it yet.  Is there some way I could get apt-get or synaptic to ignore openoffice all together and install ONLY ubuntu-desktop? Do I need to do it with dpkg?   Thanks. Oh, and off-topic, how do I get line-breaks to stay in my forum posts? I am not a fan of text blobs like this one. Paragraphs make things easier to read.

---

### Post by weeman7007 on 2009-05-28
for the off-topic answer.. just separate things out with the enter/return button.

Have you tried searching for a fix for your soundcard rather than upgrade/downgrades?

---

### Post by dzcomposer on 2009-05-28
I tried using enter, but the forum software takes the breaks out when I hit submit. EDIT: and it works in this post... WTF?

I did try to fix the soundcard. I spent hours and got nowhere, and ended up breaking networking. In the end, I just want my machine to work, so I decided to downgrade as it was not worth the hassle to fix the sound issue.

---

### Post by weeman7007 on 2009-05-28
ahh ok, it is a pain when ubuntu breaks something that used to work isn't it lol. sorry i can't be of more help. What does ubuntu-desktop actually do? and can it function without it?

---

### Post by ghen on 2009-05-28
I wonder if you install the .deb of openoffice if it will save your settings and not uninstall with ubuntu-desktop.

that might give you both 2.4 and 3.1 on reinstall though if my theory is correct.

Or another alternative to what you're looking for is to figure out what you want to save (settings, etc) and copy it elsewhere on the file system before reinstall. Tedious, sure.. but for some things its the only way.

---

### Post by dzcomposer on 2009-05-28
So there is no way for this package manager to force a single package?

---

### Post by ghen on 2009-05-28
Oh I'm sure there's a correct way to install just what you want, I was just thinking outside the box a little because I don't know the right answer as a linux newbie.

What about ubuntu-core, gnome, or gnome-core? I don't know what those packages include but it should be less than ubuntu-desktop.


edit: oh wait, here we go! This is from a server FAQ:

[quote=http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html]If you wan to install a graphical desktop manager without some of the desktop addons like Evolution and OpenOffice, but continue to use the server flavor kernel use the following command
sudo aptitude  install --no-install-recommends ubuntu-desktop[/quote]

---

### Post by ptn107 on 2009-05-28
ubuntu-desktop is a metapackage[1] for the Ubuntu desktop edition including the GNOME desktop environment and all the productivity software.  It alone does nothing, and it is safe not to have it installed.  If you upgrade in the future to a new Ubuntu release, ubuntu-desktop must be installed to assure a smooth upgrade.

[1][https://help.ubuntu.com/community/MetaPackages#Ubuntu%20System%20Metapackages]("https://help.ubuntu.com/community/MetaPackages#Ubuntu%20System%20Metapackages")

---

### Post by ghen on 2009-05-28
> **ptn107 said:**
> ubuntu-desktop is a metapackage[1] for the Ubuntu desktop edition including the GNOME desktop environment and all the productivity software.

Do you know of a location where metapackages are listed broken down into their components? That would solve this thread.

---

### Post by dzcomposer on 2009-05-28
> **ghen said:**
> Oh I'm sure there's a correct way to install just what you want, I was just thinking outside the box a little because I don't know the right answer as a linux newbie.

What about ubuntu-core, gnome, or gnome-core? I don't know what those packages include but it should be less than ubuntu-desktop.


edit: oh wait, here we go! This is from a server FAQ:

That did it!

Now, that brings forward this question: Why wasn't that option described in the man page?

---

