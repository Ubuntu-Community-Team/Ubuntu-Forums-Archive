---
title: "Icons on Toolbar in Fluxbuntu look broken"
date: 2008-03-25
forum: Desktop Environments
---

### Post by ptero on 2008-03-25
Like said in the subject, the icons on the toolbar look broken. All the other graphics (like, in programs ;) ) look fine, though. so, err... what may be the problem?

---

### Post by kerry_s on 2008-03-25
that's a problem with the way it was compiled, there is another thread about the exact same thing, the fix was to compile fluxbox yourself.

use the search function to find that thread.

---

### Post by ptero on 2008-03-25
damn... i wanted to remove installed fluxbox first and now i got a trouble and apt-get doesn't wont to do anything.
it wanted to remove fluxbuntu-default-settings as well, but didn't manage to ;)
now i always get following respond from apt-get:
```
Removing fluxbuntu-default-settings ...
dpkg-divert: --remove needs a single argument

Usage: dpkg-divert [<option> ...] <command>

Commands:
  [--add] <file>           add a diversion.
  --remove <file>          remove the diversion.
  --list [<glob-pattern>]  show file diversions.
  --truename <file>        return the diverted file.

Options:
  --package <package>      name of the package whose copy of <file> will not
                             be diverted.
  --local                  all packages' versions are diverted.
  --divert <divert-to>     the name used by other packages' versions.
  --rename                 actually move the file aside (or back).
  --admindir <directory>   set the directory with the diversions file.
  --test                   don't do anything, just demonstrate.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.

When adding, default is --local and --divert <original>.distrib.
When removing, --package or --local and --divert must match if specified.
Package preinst/postrm scripts should always specify --package and --divert.
dpkg: error processing fluxbuntu-default-settings (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 fluxbuntu-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
how do i remove fluxbuntu-default-settings from apt-get's queue?

---

### Post by kerry_s on 2008-03-25
try running->
**sudo apt-get -f install**

---

### Post by ptero on 2008-03-25
nah, it doesn't help...

---

### Post by ptero on 2008-03-25
which genius designed this [beeeeeep] package system?!

i started aptitude, told it to keep fluxbuntu-default-settings, not to remove anything automatically and to install fluxbox again. no matter what i do - i get this damned error message again!!!
aptitude tells me 
```
E: I wasn't able to locate file for the fluxbuntu-default-settings package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download"
```
whoever designed this system needs to do better (yes, i know, i coudn't, nevertheless i'm pretty angry right now).

---

### Post by ptero on 2008-03-26
well... the solution was pretty easy. i just had to reinstall fluxbox and fluxbuntu-default-settings from cd with dpkg -i. now apt works again...

---

