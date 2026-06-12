---
title: "InkScape 0.43"
date: 2005-11-24
forum: Deferred/Invalid Requests
---

### Post by GothicX on 2005-11-24
November 21, 2005

Inkscape 0.43 is now available thanks to the work of many developers and the sponsorship of Google's Summer of Code program which sponsored four students to work on features for Inkscape. The main new features in this release are:

    * Connectors: Objects can be connected using auto-routing lines.
    * Inkboard Collaborative Editing: You can connect to other Inkscape users over a network and edit a shared document.
    * Pressure and Tilt Sensitivity: The calligraphy tool may now use a tablet pen with pressure and tilt support.
    * Better Node Editing: You can now drag, bend, and stretch a Bezier curve by any point and not only by a node.
    * New Extensions: There are now extensions for envelope distortion, whirling, and adding nodes.
    * SVG Compliance: There is now additional support for the viewBox element improving SVG compatibility.
    * There is an online book, "A Guide to Inkscape", which has been updated to cover the 0.43 features. 

[http://inkscape.sourceforge.net/](http://inkscape.sourceforge.net/)

---

### Post by jdong on 2005-11-24
Not in Dapper.

---

### Post by kperkins on 2005-12-06
I have a how to [here]("http://www.ubuntuforums.org/showthread.php?t=93233") on installing it in Breezy. (I, also, packaged up the dependencies that you need, but, aren't in breezy, with the Inkscape deb, in a tar.gz, that you can download.) Working great for me.  
Use at your own risk, etc....

---

### Post by Who on 2005-12-06
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=inkscape&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=inkscape&searchon=names&subword=1&version=dapper&release=all)

Is Inkscape going to be backported now it is in Dapper, or are there other reasons for it to be deffered?

---

### Post by ember on 2005-12-06
It builds with some non-critical errors. I just tried it for myself.

Interested users can download my package at:

[www.doeweling.com/dists/breezy-backports-staging/universe/inkscape_0.43-1build1_i386.deb]("www.doeweling.com/dists/breezy-backports-staging/universe/inkscape_0.43-1build1_i386.deb")

No warranty at all. Yet it works for me, so you may give it a try.

Best,
ember

---

### Post by BobSongs on 2006-03-28
Okay. You've got Breezy Badger installed and you've read in this very thread something about ... extensions. But where are they?

Inkscape is very versatile but it might be fairly soon before you reach the limits of what it can do. So a few extra tools with some cool features wouldn't be too bad to raise the fun or productivity levels, right?

I'm going to assume you've got Inkscape installed. If not, download Automatix and get installing.

Now let's activate the extra effects.

[LIST=1]
[*]Shut down any running copy of Inkscape.
[*]Open an instance of Nautilus at your home folder (Places &#8594; Home Folder).
[*]When Nautilus opens cause it to display hidden folders (View &#8594; Show Hidden Folders).
[*]The right-hand side of Nautilus should fill with a few more folders, folders that begin with a dot. Scroll down until you locate **.inkscape** and double click it to open it.
[*]Inside that folder should be a file called **preferences.xml**. Edit that file with your favorite text editor or the Ubuntu default editor called **Gedit**.
[*]Scroll down in the file to near the bottom. There should be an entry that looks like:```
<group
id="extensions"
show-effects-menu="0"
org.inkscape.print.ps.bitmap="0"
org.inkscape.print.ps.resolution="72"
org.inkscape.print.ps.destination="lp -P [printer]" />
```Replace **show-effects-menu="0"** with **show-effects-menu="1"** and save the file.
[/LIST]

Now open Inkscape and enjoy the various goodies found under the new menu item called **Effects**.

---

