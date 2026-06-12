---
title: "Adding new themes?"
date: 2009-05-20
forum: Desktop Environments
---

### Post by Old *ix Geek on 2009-05-20
From **System | System Settings | Appearance | Style**, there are choices for "Widget Style," such as Klearlooks, Motif, and Oxygen.  I want to add more themes, but there is no option on that page to do so.  Where are these stored?  Where can I find new ones?  And when I do find new ones, do I simply place them where the others are stored and then they'll show up in the list of choices?  Or do they have to be installed somehow?

Same question regarding **System | System Settings | Appearance | Windows**; this is where choices such as Keramik, Modern System, and Ozone are listed.  How/where/etc. do I add new themes?

---

### Post by benerivo on 2009-05-20
You have to download and install them. Some are in the repositories (search for kde-style and kwin-style), and others are on websites such as kde-look.org. They are really packages that have to be installed, unlike gtk themes that are just 'dragged and dropped'.

---

### Post by Old *ix Geek on 2009-05-20
> **benerivo said:**
> You have to download and install them. Some are in the repositories (search for kde-style and kwin-style), and others are on websites such as kde-look.org. They are really packages that have to be installed, unlike gtk themes that are just 'dragged and dropped'.Well, I've been to kde-look.org many times and usually end up with a plain text file when I download a theme.  For example, I downloaded Bespin Metal just now, [http://kde-look.org/content/show.php/Bespin+Metal+%2B+Glaciar+colors?content=104576](http://kde-look.org/content/show.php/Bespin+Metal+%2B+Glaciar+colors?content=104576) and the tar file contains two plain text files, 79052-Glacier.colors and metal.bespin.  How are these installed so that they appear in the tabs I mentioned in my OP?

---

### Post by benerivo on 2009-05-20
With this Bespin example, it's not completely straightforward. As with many kde4 styles it comes in the format of a .tar.gz file that is suitable for command line installation on any linux os. The style you have found is actually just a config file for the bespin style. It is not the style itself. (ie. it's a bit like a theme/skin for firefox, but it isn't firefox itself). The link you want to get to is this...
[http://cloudcity.sourceforge.net/download.php](http://cloudcity.sourceforge.net/download.php)
Before i went any further i had to install a package called subversion from the repositories. Then from a terminal i did```
svn co https://cloudcity.svn.sourceforge.net/svnroot/cloudcity
```(as stated on that link) and this downloaded the latest bespin release to a folder called cloudcity in my home folder. I followed the instructions (given on the link above) starting from the bit that says "Enter the just created bespin directory:- cd cloudcity", and the installation worked for me. It was then available in the system settings of kde, both as a style and a window decoration. You will need some packages installed to get this to work. I think you'll need at least gcc and make (available from the repositories).

EDIT - Bespin is available in the repositories. Check here...
[http://packages.ubuntu.com/search?keywords=bespin&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=bespin&searchon=names&suite=jaunty&section=all)

---

