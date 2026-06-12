---
title: "mythtv synaptic package"
date: 2005-12-07
forum: General Help
---

### Post by lobbster on 2005-12-07
does anyone have the package for myth tv or a guid on how to install it with out synapitc.

thnx 
lobbster
[www.frontlinetech.blogspot.com](www.frontlinetech.blogspot.com)

---

### Post by SleepyHollow on 2005-12-07
[QUOTE=lobbster]does anyone have the package for myth tv or a guid on how to install it with out synapitc.
[/QUOTE]

Still no solution? I asked and heared the answer: packages are broken nobody will fix it! Compile it at yourself. This is no solution for me. If there is a binary package I would try it. :confused:

---

### Post by Drain on 2005-12-07
[QUOTE=SleepyHollow]Still no solution? I asked and heared the answer: packages are broken nobody will fix it! Compile it at yourself. This is no solution for me. If there is a binary package I would try it. :confused:[/QUOTE]

Yes, there are no pre-built packages for Breezy on an AMD64.  (The packages are available in the universe/multiverse repositories for Breezy on x86, however). It is not too difficult to build your own packages.  

1. Get the piece(s) you need to make the packages. 
**$ sudo apt-get build-dep mythtv**

2. Get the actual packages (you'll get 3 files, a .tar, .dsc, and .diff.gz).
**$ sudo apt-get source mythtv-frontend**

3. Edit the debian/rules file, and change the line that reads: 
"cpu=i486 --tune=pentium4 --enable-mmx \" 
to 
"cpu=x86_64 --tune=generic --enable-mmx \" 

and comment out "# --enable-opengl-vsync \"

4. Build the downloaded packages. 
**$ sudo apt-get -b source mythtv-frontend**

Other missing mythtv packages are handled in a similar way - get the build-dependencies, and do the "apt-get - b source" command again.  The hard part for me was dealing with the MySQL database during the rest of the install, but they follow the other MythTV guides, regardless of being x86 or AMD64. 

I don't know if that will help you much. But you're not completely stuck - it just depends on how much work you want to do to get things going. (and also how much you're willing to format  the computer and start over if necessary. ;-) ) Good luck!

---

