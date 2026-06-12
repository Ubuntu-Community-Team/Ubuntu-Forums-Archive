---
title: "Package is &quot;stuck&quot;, can't be uninstalled or unmarked"
date: 2007-12-10
forum: Desktop Environments
---

### Post by Landslide on 2007-12-10
I downloaded Fluxbuntu and installed the desktop package from the CD to try it out, but then I tried removing fluxbuntu-default-settings, and for some reason it didn't uninstall properly. The uninstall script returns with "error code 2", which isn't the most helpful error message.

The weird thing is, I can't even just keep it installed by unmarking the change, and it's keeping Update Manager from being able to update software, and keeping me from installing any new software with apt-get or Synaptic.

[Here]("http://realmofshazbot.com/Screenshot-update-manager.png")'s the error message I get when I run Update Manager. It tells me to run "sudo apt-get install -f" which gives this output:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  fluxbuntu-default-settings
0 upgraded, 0 newly installed, 1 to remove and 61 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 328kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 140619 files and directories currently installed.)
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

And when I try to "unmark" the package in Synaptic, it doesn't do anything. How do I fix this? I need to install some new packages and get all my updates.

---

### Post by shae on 2007-12-11
I would try the following:
```
sudo dpkg --force-remove-reinstreq fluxbuntu-default-settings
```

---

### Post by Landslide on 2007-12-11
That command returns this output:
```
$ sudo dpkg --force-remove-reinstreq fluxbuntu-default-settings
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

I don't know a whole lot about dpkg, so I don't know how to interpret this. Can anyone help?

---

### Post by Landslide on 2007-12-11
After talking to the people in #fluxbuntu, they've told me that installing packages with APT from the installation CD is "not supported." I wish they'd made that more clear on their website, but I managed to fix it by editing /var/lib/dpkg/info/fluxbuntu-default-settings.postrm and commenting out everything between the "then" and the "fi" except for the last line, then re-running "sudo apt-get remove fluxbuntu-default-settings".

Inconvenient, but I did learn something about Debian install/uninstall scripts which was a good experience.

---

### Post by HeyGabe on 2008-01-26
I can't get this package uninstalled either. Even following your instructions. What I really want is not to have that gawdawful Fluxbuntu Color Scheme haunt me in Gnome Aps.
please helP!

---

### Post by enbuyukfener on 2008-02-27
Probably too late but if anyone else like me finds this through a search, here is a little detailed howto based on Landslide's last post which was a great help (thanks!). I'm posting this due to the missing --remove in the command above and the fact that I had to remove a bit more from the post-remove file.

```
# if you haven't done so already:
sudo aptitude remove fluxbuntu-default-settings

# remove or comment lines from "if $1=remove" to "fi" inclusive
sudo nano /var/lib/dpkg/info/fluxbuntu-default-settings.postrm

# force removal
sudo dpkg --force-remove-reinstreq --remove fluxbuntu-default-settings
```

---

