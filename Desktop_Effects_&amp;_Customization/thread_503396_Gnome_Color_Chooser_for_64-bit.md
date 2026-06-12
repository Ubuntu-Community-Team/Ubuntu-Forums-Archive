---
title: "Gnome Color Chooser for 64-bit"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by abrichr on 2007-07-17
Is there a way to make gnome color chooser work under the AMD64 architecture?  When I try to install the 32-bit .deb by double-clicking on it in nautilus, I get an error:

"Error: Wrong architecture 'i386'"

Using gdebi from the console:

"This package is uninstallable
Wrong architecture 'i386'"

---

### Post by abrichr on 2007-07-17
Ok, so I tried:

```
sudo dpkg -i --force-architecture gnome-color-chooser_0.2.2-1_feisty_i386.deb.deb
```

And I got:

```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package gnome-color-chooser.
(Reading database ... 105818 files and directories currently installed.)
Unpacking gnome-color-chooser (from gnome-color-chooser_0.2.2-1_feisty_i386.deb.deb) ...
dpkg: dependency problems prevent configuration of gnome-color-chooser:
 gnome-color-chooser depends on libcairomm-1.0-1; however:
  Package libcairomm-1.0-1 is not installed.
 gnome-color-chooser depends on libgconfmm-2.6-1c2 (>= 2.10.0-3); however:
  Package libgconfmm-2.6-1c2 is not installed.
 gnome-color-chooser depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not installed.
 gnome-color-chooser depends on libglibmm-2.4-1c2a; however:
  Package libglibmm-2.4-1c2a is not installed.
 gnome-color-chooser depends on libgnome-vfsmm-2.6-1c2a (>= 2.14.0); however:
  Package libgnome-vfsmm-2.6-1c2a is not installed.
 gnome-color-chooser depends on libgnomecanvasmm-2.6-1c2a; however:
  Package libgnomecanvasmm-2.6-1c2a is not installed.
 gnome-color-chooser depends on libgnomemm-2.6-1c2a (>= 2.16.0); however:
  Package libgnomemm-2.6-1c2a is not installed.
 gnome-color-chooser depends on libgnomeuimm-2.6-1c2a (>= 2.16.0); however:
  Package libgnomeuimm-2.6-1c2a is not installed.
 gnome-color-chooser depends on libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2a is not installed.
dpkg: error processing gnome-color-chooser (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-color-chooser

```

So I installed the dependencies using apt-get no problem.. Now when I try to run gnome-color-chooser from the terminal, however:

```
gnome-color-chooser: error while loading shared libraries: libgnomeuimm-2.6.so.1: cannot open shared object file: No such file or directory

```

...Except that I just installed it.  Is this also an architecture thing?  Or is it something else entirely?  Is there perhaps a 64-bit application that is similiar to gnome-color-chooser that I could use instead?

---

### Post by bwhitaker on 2007-09-09
It's a 32bit application so it's looking for 32bit libraries. 


It also doesn't seem to be ready to easily compile from source for 64bit systems either.  At least not without changing the configure and make scripts.

---

### Post by JackTheDipper on 2007-09-17
Hi,

could you tell me which changes have to be made so that i can apply them to upstream? Haven't heard of any 64bit problems yet and there are already 64bit binary packages out there.

best regards,
Jack ;-)

---

