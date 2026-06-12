---
title: "PyMOL symmetry operations/axes?"
date: 2012-02-11
forum: Education &amp; Science
---

### Post by JayLR on 2012-02-11
I'm using Ubuntu 11.10 with PyMOL 1.4.1 and would like to be able to visualize symmetry operations and axes with it.  Does anyone know how this is possible?

I have attempted to install cctbx crystallography toolbox, but it doesn't seem to have an ubuntu installation.  
[http://cci.lbl.gov/cctbx_build/](http://cci.lbl.gov/cctbx_build/)
Can anyone point me in the right direction?

---

### Post by Chronon on 2012-02-18
I haven't used either of these, but I did pop over to the cctbx site and saw that they only have pre-built packages for Fedora/CentOS/RedHat, OSX and Windows.  

Did you try the "Self-extracting cctbx sources for Unix"?

Alien is also an option for converting .rpm to .deb.

---

### Post by JayLR on 2012-02-18
I have not. First off, unfortunately, it is almost entirely Macintosh and Windows at work.  I am extremely new to linux, and it will probably show in this post. 

I have PyMol functioning perfectly, and have followed this link [http://sage.ucsc.edu/~wgscott/xtal/wiki/index.php/CCP4-6.1.0_on_Ubuntu_Ibex]("http://sage.ucsc.edu/%7Ewgscott/xtal/wiki/index.php/CCP4-6.1.0_on_Ubuntu_Ibex")
using the °source /usr/local/xtal/ccp4-6.1.0/include/ccp4.setup-csh° command.

Now I am uncertain of what to do next.  I am pretty sure I need to edit my $PATH somehow.

The site here [http://www.pymolwiki.org/index.php/CCTBX](http://www.pymolwiki.org/index.php/CCTBX)

I changed my pymol.com.linux-rh7x file from °exec /usr/bin/python $PYMOL_PATH/modules/pymol/__init__.py "$@"°
to exec °python $PYMOL_PATH/modules/pymol/__init__.py "$@"° with no luck. 

Am I on the wrong track?

---

