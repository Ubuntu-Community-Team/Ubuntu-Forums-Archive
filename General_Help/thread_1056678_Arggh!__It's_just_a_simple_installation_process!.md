---
title: "Arggh!  It's just a simple installation process!"
date: 2009-02-01
forum: General Help
---

### Post by YellowHammer on 2009-02-01
About once a year, for the past 7 years I keep trying linux. Each time it always seems too clunky.  This time I've installed the latest Ubuntu 32-bit.  Here's my trouble:  I'm trying to install Lincity.  Upon installation, it found I was missing some SDL stuff (whatever it is).   I use the package manager to install what it needs, and then try again to install lincity.  Again it's missing more SDL stuff.  So I add the new package, and try again.  It needs MORE sdl stuff.   I add the package, and  try again.  

Finally I come to sdl_gfx.  I add this package, but lincity says it's the wrong version.  I visit the sdl_gfx website, and sure enough they have 2.0.18 (where 2.0.13 is available in package manager).  So I download 2.0.18 in tar.gz format.  I unzip/tar the files, and now I have a folder full of junk.  I see an INSTALL file, but it won't execute.  Next I try ./configure.  It works, until it says it's missing SDL 1.2


I'm not a big MS fan, and I really hate my old XP box.  But at least when I click on "Install" or "setup"... IT WORKS!  ARRGH!  Someone help this frustrated Linux user wannabe!   I come from the day of DOS 5.0, and enjoy a good challenge, but I also appreciate a simple installation process.  An hour is a bit long to install a game (and I'm not done yet)

---

### Post by taurus on 2009-02-01
When you compile something from source and it complains about missing a library, you have to install the library _plus_ the developing package, -dev, also.

---

