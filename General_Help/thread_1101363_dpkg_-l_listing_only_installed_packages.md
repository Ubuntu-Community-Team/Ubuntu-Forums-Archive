---
title: "dpkg -l listing only installed packages"
date: 2009-03-20
forum: General Help
---

### Post by bwm71 on 2009-03-20
Brand new to Ubuntu and the install process has no doubt been the easiest of all of the distributions I've tried.  One question about dpkg.  On my Debian systems, "dpkg -l" lists all available packages which seems to be the expected behavior in Ubuntu.  However, on my system "dpkg -l" lists only those packages that are installed and configured.

$ dpkg -l|grep -v "^i"            
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                      Version                           Description
+++-==========================================-=================================-============================================
$

Any ideas?

Brandon

---

### Post by nothingspecial on 2009-03-20
Have you tried ```
apt-cache search *name_or_part_of_name_of_package*
```

---

### Post by bwm71 on 2009-03-20
Sure, "apt-cache search" works, but that's not what I was asking.  I'm wondering why "dpkg -l" doesn't behave according to the documentation.  "dpkg -l" is useful for not only showing available packages, but the state of installed or partially installed packages.

Brandon

---

### Post by fieroboom on 2009-03-20
If you're interested in viewing all available packages like Synaptic does when you first start it up (before a search), then first you need to update (re-synchronize) your package index:
```
sudo apt-get update
```
Then if you want to see **all** available packages, run this command:
```
grep Package /var/lib/dpkg/available
```
Or, to search for a specific keyword:
```
aptitude search <keyword>
```
Example:
```
root@pallen:~# aptitude search gedit
i   gedit                                                                             - official text editor of the GNOME desktop environment
i A gedit-common                                                                      - official text editor of the GNOME desktop environment (support files)
p   gedit-dev                                                                         - official text editor of the GNOME desktop environment (development files)
p   gedit-plugins                                                                     - set of plugins for gedit
p   gigedit                                                                           - instrument editor for Gigasampler files
p   moaggedit                                                                         - map editor for the Moagg game
```
And finally, if you want specific information about a certain package:
```
apt-cache show <package>
```
Example:
```
root@pallen:~# apt-cache show gimp
Package: gimp                     
Priority: optional
Section: graphics
Installed-Size: 12472
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Ari Pollak <ari@debian.org>
Architecture: i386
Version: 2.6.1-1ubuntu3
Replaces: gimp-data (<< 2.3.17-2), gimp-gnomevfs (<< 2.6.0), gimp-helpbrowser, gimp-libcurl (<< 2.6.0), gimp-print (<= 5.0.1-3), gimp-python (<< 2.6.0), gimp-svg, gimp-wget (<< 2.3.12-1), libgimp-perl (<= 2.0.dfsg+2.2pre1.dfsg-2)
Provides: gimp-helpbrowser, gimp-python
Depends: libgimp2.0 (>= 2.6.1), libgimp2.0 (<= 2.6.1-z), gimp-data (>= 2.6.1), gimp-data (<= 2.6.1-z), python-gtk2 (>= 2.8.0), libaa1 (>= 1.4p5), libatk1.0-0 (>= 1.20.0), libbabl-0.0-0, libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libexif12, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgegl-0.0-0, libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.1), libhal1 (>= 0.5.8.1), libjpeg62, liblcms1 (>= 1.15-1), libmng1 (>= 1.0.3-1), libpango1.0-0 (>= 1.21.6), libpng12-0 (>= 1.2.13-4), libpoppler-glib3, librsvg2-2 (>= 2.18.1), libtiff4, libwmf0.2-7 (>= 0.2.8.4), libx11-6, libxext6, libxfixes3 (>= 1:4.0.1), libxmu6, libxpm4, zlib1g (>= 1:1.1.4), python (<< 2.6), python (>= 2.5), python-support (>= 0.7.1)
Suggests: gimp-help-en | gimp-help, libgimp-perl, gimp-data-extras, gvfs-backends, libasound2, ghostscript
Conflicts: gimp-data (<< 2.3.17-2), gimp-gnomevfs (<< 2.6.0), gimp-help (<< 2+0.13-1), gimp-helpbrowser, gimp-libcurl (<< 2.6.0), gimp-print (<= 5.0.1-3), gimp-python (<< 2.6.0), gimp-svg, gimp-wget (<< 2.3.12-1), libgimp-perl (<= 2.0.dfsg+2.2pre1.dfsg-2)
Filename: pool/main/g/gimp/gimp_2.6.1-1ubuntu3_i386.deb
Size: 4366488
MD5sum: 9c04d75d06e8ea332f82080445cbb6ba
SHA1: d1bd499d10a3cd8f7455df20a80818787ac59881
SHA256: 9f126118d4e000cd8eba8574c94d9fbc61789577dea00f1ac7f449b48ca10053
Description: The GNU Image Manipulation Program
 GIMP lets you draw, paint, edit images, and much more! GIMP
 includes the functionality and plug-ins of other famous image
 editing and processing programs.
<truncated for post length>
```
[man apt-get](http://linux.die.net/man/8/apt-get)
[man apt-cache](http://linux.die.net/man/8/apt-cache)
[man dpkg](http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg)
:D
-Paul

EDIT:
Forgot to mention that you can also use wildcards in your aptitude search:
```
aptitude search '.*'
```
That will list **everything**

---

### Post by bwm71 on 2009-03-20
Maybe I'm missing something here.  As I mentioned, "dpkg -l" on my Debian systems shows all available packages.  Furthermore, if this isn't possible on Ubuntu, why does the output of dpkg show at the top of its output the status legend which includes indicators for packages that aren't "ii"?

I'm not trying to be argumentative.  I'm just trying to understand this different behavior of dpkg.

Brandon

---

### Post by madscientist on 2009-04-02
I can't remember how "dpkg -l" by itself used to work on Debian; I don't think I ever used it.  However, I use "dpkg -l <pattern>" all the time and that does report uninstalled packages as well:

```
$ dpkg -l man\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  man            <none>         (no description available)
un  man-browser    <none>         (no description available)
ii  man-db         2.5.1-3        on-line manual pager
ii  manpages       2.77-1         Manual pages about using a GNU/Linux system
un  manpages-de    <none>         (no description available)
ii  manpages-dev   2.77-1         Manual pages about using GNU/Linux for devel
un  manpages-es    <none>         (no description available)
un  manpages-es-ex <none>         (no description available)
    ...
```I have noticed that not all packages are listed here though: sometimes when I'm looking for a particular package I can't find it in this output, while aptitude search does find it.  I don't know what the difference is between those that are and aren't, but IIRC I had the same behavior under Debian.

If it really does work differently on Debian and Ubuntu then I would recommend filing a bug in launchpad.

---

### Post by bwm71 on 2009-04-07
I'm almost positive that "dpkg -l" by itself on Debian produced a list of all packages.  I'll have to check on my Debian machine when I get home.

At any rate, the more I use Ubuntu, the more I think it's the best distribution yet.

Brandon

---

### Post by GeeZor on 2009-04-07
Sounds interesting..

Just as a second opinion i will do the same thing tomorrow...
using Debian Etch at work..

Keep you posted!

---

