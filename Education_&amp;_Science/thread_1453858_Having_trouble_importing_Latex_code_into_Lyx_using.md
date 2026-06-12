---
title: "Having trouble importing Latex code into Lyx using tex2lyx"
date: 2010-04-13
forum: Education &amp; Science
---

### Post by TheOneEyedMan on 2010-04-13
Tried directly using tex2lyx as well as using File-Import-Latex (plain) and both give me problems. I've tried known working latex code on the Internet but that doesn't work either, so I don't think I have a bad input on my end. 

Within Lyx, the version shows up as 1.6.0 while from synaptic package manager the installation is package 1.6.4-1ubuntu1. 

The error message from lyx is:
 "An error occurred whilst running tex2lyx -f 'Latex_Output_for_Housing_Class_1.tex'

The error from the command line (tex2lyx -f Latex_Output_for_Housing_Class_1.tex tmp.lyx ) is more elaborate but no more helpful to me:
[INDENT]'import site' failed; use -v for traceback
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/share/lyx/scripts/layout2layout.py", line 15, in <module>
    import os, re, string, sys
  File "/usr/lib/python2.6/os.py", line 49, in <module>
    import posixpath as path
  File "/usr/lib/python2.6/posixpath.py", line 16, in <module>
    import warnings
  File "/usr/lib/python2.6/warnings.py", line 6, in <module>
    import linecache
ImportError: No module named linecache
Could not run layout conversion script layout2layout.py.
We failed to find the layout '' in the layout list. You MUST investigate!
Segmentation fault[/INDENT]

Any advice on how to fix this problem or work around it? Thanks for the help.

---

### Post by TheOneEyedMan on 2010-04-13
I've attached the source document mentioned above to help with diagnosis. The extension must be changed from txt to tex or the code modified for the existing file.  

I wasn't sure what category to file this under. If it was an incorrect classification, I apologize.

---

### Post by TheOneEyedMan on 2010-05-03
I am still having this problem. I wonder if anyone knows what is going on. I asked on the Lyx mailing list and they suggested there was a problem with my Python installation but could not help further. 

I tried solving the problem by upgrading to Lucid Lynx but that did not help. 

Anyone have any ideas?

---

### Post by TheOneEyedMan on 2010-05-06
This was recently moved into the Education & Science forum and I wanted to put a new post in it to bump it.

Can anyone help me out?

---

### Post by happyhamster on 2010-05-08
> **TheOneEyedMan said:**
> Within Lyx, the version shows up as 1.6.0 while from synaptic package manager the installation is package 1.6.4-1ubuntu1.
Does that mean the package is 'pinned' in your package-manager? (In other words: why isn't the package the newest version?)
 
> 
  File "/usr/lib/python2.6/warnings.py", line 6, in <module>
    import linecache
ImportError: No module named linecache
- Is there a linecache module on your system? To search for it, first update the search database (it could take some time):

sudo updatedb

- then do the search:

locate linecache.py

---

### Post by TheOneEyedMan on 2010-05-08
Just looks installed (solid green box)

Results of locate linecache.py:
/usr/lib/python2.6/linecache.py
/usr/lib/python2.6/linecache.pyc
/usr/share/lyx/scripts/linecache.py

---

### Post by happyhamster on 2010-05-08
- What lyx versions are outputted by:

apt-cache policy lyx

- Which python versions are installed? Type:

python

- and press tab twice (fast) to see all executable python files.

---

### Post by TheOneEyedMan on 2010-05-08
Results of apt-cache policy lyx

lyx:
  Installed: 1.6.5-1ubuntu1
  Candidate: 1.6.5-1ubuntu1
  Version table:
 *** 1.6.5-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages
        100 /var/lib/dpkg/status

The tab-tab thing didn't work. All I get is two tabs on the python command line. 
When I run python from the command line I get the following output. 

Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.

---

### Post by happyhamster on 2010-05-09
Just type "python" into a gnome/bash terminal (not into a python command line). Instead of pressing Enter, press tab twice to show all possible autocomplete entries. Or just do a manual search in synaptic for python.

Anyway, if there are multiple versions of python, it could be that lyx is somehow calling a version other than 2.6.5. A good test would be to get rid of the other versions completely (if possible, of course), and perhaps re-install lyx.

---

### Post by TheOneEyedMan on 2010-05-09
Ah, now I understand. He following is my list of installed packages that include the word "python" in the package name. Nothing jumps out at me as being an old version. 

diveintopython
idle-python2.6
ipython
libboost-python1.40.0
libpython2.6
python
python2.6
python2.6-doc
python2.6-examples
python2.6-minimal
python-appindicator
python-apport
python-apt
python-aptdaemon
python-aptdaemon-gtk
python-at-spi
python-avahi
python-beautifulsoup
python-bittorrent
python-brasero
python-brlapi
python-bugbuddy
python-cairo
python-central
python-cherrypy3
python-clientform
python-compizconfig
python-configglue
python-couchdb
python-crypto
python-cssutils
python-cups
python-cupshelpers
python-daap
python-dateutil
python-dbus
python-debian
python-desktopcouch
python-desktopcouch-records
python-django
python-django-tagging
python-egenix-mxdatetime
python-egenix-mxtools
python-encutils
python-evince
python-evolution
python-farsight
python-foolscap
python-fstab
python-gconf
python-gdbm
python-glade2
python-gmenu
python-gnome2
python-gnome2-desktop
python-gnomeapplet
python-gnomecanvas
python-gnomedesktop
python-gnomekeyring
python-gnomeprint
python-gnupginterface
python-gobject
python-gpod
python-gst0.10
python-gtk2
python-gtk2-doc
python-gtk2-tutorial
python-gtkglext1
python-gtkmozembed
python-gtksourceview2
python-gtkspell
python-gtop
python-httplib2
python-ibus
python-imaging
python-indicate
python-kde4
python-keybinder
python-launchpad-integration
python-launchpadlib
python-lazr.restfulclient
python-lazr.uri
python-libtorrent
python-libuser
python-libxml2
python-louis
python-lxml
python-mako
python-matplotlib-doc
python-mechanize
python-mediaprofiles
python-metacity
python-minimal
python-mmkeys
python-mutagen
python-newt
python-notify
python-numeric
python-numpy
python-numpy-doc
python-oauth
python-opengl
python-openssl
python-packagekit
python-papyon
python-pexpect
python-pkg-resources
python-problem-report
python-protobuf
python-pyatspi
python-pycurl
python-pygoocanvas
python-pyinotify
python-pyorbit
python-pyparsing
python-pypdf
python-pyrex
python-pysqlite2
python-qt4
python-rdflib
python-rsvg
python-scipy
python-sexy
python-simplejson
python-sip
python-smartpm
python-smbc
python-software-properties
python-speechd
python-support
python-telepathy
python-tk
python-totem-plparser
python-twisted-bin
python-twisted-core
python-twisted-names
python-twisted-web
python-tz
python-ubuntuone
python-ubuntuone-client
python-ubuntuone-storageprotocol
python-uno
python-virtkey
python-vte
python-wadllib
python-webkit
python-wnck
python-wxgtk2.6
python-wxgtk2.8
python-wxversion
python-xapian
python-xdg
python-xkit
python-xlib
python-zope.interface

---

### Post by happyhamster on 2010-05-09
- Perhaps a permission or path problem then? Does:

import linecache

- work in a python console? Also, take a look at:

ls -l /usr/lib/python2.6/linecache.py

- On my system the permissions for that file are: -rw-r--r-- root root. Also, what is in your path:

echo $PATH

- Are there other environment variables you have set manually?

> 
Results of locate linecache.py:
/usr/lib/python2.6/linecache.py
/usr/lib/python2.6/linecache.pyc
/usr/share/lyx/scripts/linecache.py 
- Get rid of that last file (temporarily), and test if tex2lyx will run in that case. (Just rename it, or move it to your home folder or such.)

Good luck.

---

### Post by TheOneEyedMan on 2010-05-09
Running python...
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import linecache
>>>

Does that mean it worked?

ls -l /usr/lib/python2.6/linecache.py
-rw-r--r-- 1 root root 4.2K 2010-04-16 07:41 /usr/lib/python2.6/linecache.py


I tried the rename:
cd /usr/share/lyx/scripts$
sudo mv linecache.py linecache_old.py

Reran: tex2lyx -f Latex_Output_for_Housing_Class_1.tex tmp.lyx

Results:
Creating file /home/bkay/Documents/Macro/Predicting_housing_prices_with_rates_and_risk/tmp.lyx
'import site' failed; use -v for traceback
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/share/lyx/scripts/layout2layout.py", line 15, in <module>
    import os, re, string, sys
  File "/usr/lib/python2.6/os.py", line 49, in <module>
    import posixpath as path
  File "/usr/lib/python2.6/posixpath.py", line 16, in <module>
    import warnings
  File "/usr/lib/python2.6/warnings.py", line 6, in <module>
    import linecache
ImportError: No module named linecache
Could not run layout conversion script layout2layout.py.
We failed to find the layout '' in the layout list. You MUST investigate!
Segmentation fault

Results of echo $PATH
/home/bkay/bin:/home/bkay/bin::/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/stata:/usr/local/ampl:/usr/local/knitro/knitroampl:

Other environmental variables:
LD_LIBRARY_PATH=/usr/local/knitro/lib:/usr/local/ampl:/usr/local/tomlab/shared:/usr/local/tomlab/mex:/usr/lib:

MATLABPATH=/home/bkay/Documents/Matlab
MATLAB_USE_USERPATH=1
ZIENA_LICENSE=/usr/local/ampl/ziena_license.txt
LYX_DIR_15x=/usr/share/lyx
PYTHONPATH=/usr/lib/python2.6

---

### Post by happyhamster on 2010-05-10
> **TheOneEyedMan said:**
> Running python...
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import linecache
>>>

Does that mean it worked?
Yes, there's no complaint, so the module is visible in this case.

> 
Reran: tex2lyx -f Latex_Output_for_Housing_Class_1.tex tmp.lyx

- Try running with the -d (debugging) switch as well. And take a look if there are rogue "site.py" files:

locate site.py

> 
Results of echo $PATH
/home/bkay/bin:/home/bkay/bin::/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/stata:/usr/local/ampl:/usr/local/knitro/knitroampl:

Woah, I haven't seen such a heavily modified system before I think. Is "/home/bkay/bin:/home/bkay/bin::" intentional? Because the double colons mean that the current working directory is in your path IIRC, which seems off. Same with the last colon in "/usr/local/knitro/knitroampl:" (because it isn't followed by a directory).

---

### Post by TheOneEyedMan on 2010-05-10
Results of  locate site.py
[INDENT]/etc/python2.4/site.py
/etc/python2.5/site.py
/usr/lib/pymodules/python2.6/Xlib/ext/composite.py
/usr/lib/pymodules/python2.6/Xlib/ext/composite.pyc
/usr/lib/pymodules/python2.6/cherrypy/tutorial/tut04_complex_site.py
/usr/lib/pymodules/python2.6/cherrypy/tutorial/tut04_complex_site.pyc
/usr/lib/pymodules/python2.6/smart/channels/slack_site.py
/usr/lib/pymodules/python2.6/smart/channels/slack_site.pyc
/usr/lib/python2.6/site.py
/usr/lib/python2.6/site.pyc
/usr/share/doc/python-cssutils/examples/website.py.gz
/usr/share/pyshared/Xlib/ext/composite.py
/usr/share/pyshared/cherrypy/tutorial/tut04_complex_site.py
/usr/share/pyshared/smart/channels/slack_site.py[/INDENT]


It looks like those first two are rouge from earlier versions.

I went into the /etc direcory and ran /etc$ ls py* with the following results. Could any of that matter?
[INDENT]python:
total 4.0K
-rw-r--r-- 1 root root 94 2007-04-15 04:51 debian_config

python2.4:
total 20K
-rw-r--r-- 1 root root 155 2008-04-21 04:22 sitecustomize.py
-rw-r--r-- 1 root root 15K 2007-04-12 14:22 site.py

python2.5:
total 20K
-rw-r--r-- 1 root root 155 2008-04-21 05:47 sitecustomize.py
-rw-r--r-- 1 root root 15K 2007-04-12 14:12 site.py

python2.6:
total 4.0K
-rw-r--r-- 1 root root 155 2009-04-18 19:50 sitecustomize.py

python3.0:
total 4.0K
-rw-r--r-- 1 root root 155 2009-04-15 10:25 sitecustomize.py

python3.1:
total 4.0K
-rw-r--r-- 1 root root 155 2009-10-11 20:23 sitecustomize.py

[/INDENT]

I'd having trouble with the tex2lyx d mode. Can you tell me what I'm doing wrong?

Results of: tex2lyx -df -o "~/Documents/macro/Predicting_housing_prices_with_rates_and_risk" -r "myenv" Latex_Output_for_Housing_Class_4.tex > foo.debug  

Creating file /home/bkay/Documents/Macro/Predicting_housing_prices_with_rates_and_risk/-o
Could not open input file "/home/bkay/Documents/Macro/Predicting_housing_prices_with_rates_and_risk/-df" for reading.


No my path just seems to have some duplication in it. I fixed it but the error remains.
echo $PATH

/home/bkay/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/stata:/usr/local/ampl:/usr/local/knitro/knitroampl:

---

### Post by happyhamster on 2010-05-11
> **TheOneEyedMan said:**
> It looks like those first two are rouge from earlier versions.
Agreed. You could try deleting/renaming them, but we're getting into "let's modify until things break" territory here. I do think that some leftovers from previous or even newer (3+) pythons are interfering with the default one, perhaps in combination with pathing or permission issues. But I have no easy recommendation on how to solve that. Hunting down and cleaning python leftovers manually might just make things worse. Another try is re-installing pythons and subsequently uninstalling them completely (in the hope it will get rid of all their config files as well this time). Another one is to test tex2lyx under a default PATH.

> 
I'd having trouble with the tex2lyx d mode. Can you tell me what I'm doing wrong?

Apparently the -d switch doesn't exist for lucid. (It isn't mentioned when running "man tex2lyx" anymore.) I didn't catch that.

> 
/home/bkay/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/stata:/usr/local/ampl:/usr/local/knitro/knitroampl:
There's still some duplication though :P. Anyway, the very last colon means that the current working directory is in your path. Same for:
>  
LD_LIBRARY_PATH=/usr/local/knitro/lib:/usr/local/ampl:/usr/local/tomlab/shared:/usr/local/tomlab/mex:/usr/lib:
I'm not sure if I fully understand the security implications of that, but the default linux setting is always to disallow that AFAIK.

Good luck.

---

