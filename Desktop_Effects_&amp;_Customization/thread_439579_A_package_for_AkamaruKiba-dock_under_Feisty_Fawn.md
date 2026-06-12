---
title: "A package for Akamaru/Kiba-dock under Feisty Fawn?"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by Brian Kendig on 2007-05-10
Is there a package I can download to install the Akamaru dock (which, I gather, is the same exact thing as Kiba-dock?) under Ubuntu 7.04?

I'd rather install it as a package than compile it by hand...

---

### Post by Brian Kendig on 2007-06-04
bump

---

### Post by Vich on 2007-06-24
*Taken from the wiki @ [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock")*

**Treviño** manages a repo with kiba-dock, These can be accessed by adding the following to your [FONT="Courier New"]sources.list[/FONT] file: Note: Currently, there are only 32 bit (x86) deb packages available, 64 bit users can use SVN.

   1. Open a Terminal Window.
   2. Type the following:

[FONT="Courier New"]sudo gedit /etc/apt/sources.list[/FONT]

   1. If you are using Edgy (6.10) version: Add the following lines to the end of the file:

[FONT="Courier New"]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn[/FONT]

   1. If you are using Feisty (7.04) version: Add the following lines to the end of the file:
[FONT="Courier New"]
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy[/FONT]

   1. Save and Exit Gedit.
   2. Run from the same terminal window:

[FONT="Courier New"]wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install kiba-dock kiba-dock-dev kiba-plugins
[/FONT]

**PLEASE NOTE: this is a daily svn repo, which means you're dealing with snapshots of the latest and greatest, but not always the most stable!**

After installation it can be found in Applications->Accessories

---

