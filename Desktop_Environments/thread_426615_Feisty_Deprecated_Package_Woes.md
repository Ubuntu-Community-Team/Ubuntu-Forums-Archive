---
title: "Feisty Deprecated Package Woes"
date: 2007-04-28
forum: Desktop Environments
---

### Post by iconoclasm on 2007-04-28
I recently upgraded to Feisty from Edgy via the update manager. After a few unsuccessful attempts (connection errors to the repositories), I finally got my distro updated. However, as with most distro upgrades, some packages are no longer required... fair enough. Apt-get then told me to use the 'auto-remove' command to get rid of them... except I can't. And now I can't even install or remove packages as I get a pretty severe error it seems.

Here's my sources.list:

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu feisty main restricted
deb http://ca.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

deb-src http://ca.archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

deb-src http://ca.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```

And here's the error output from running 'sudo apt-get autoremove' :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  acroread-escript x11proto-xext-dev libflac++5c2 libapr0 libsqlite0
  libwavpack0 libsvn0 libmono-sharpzip0.6-cil libwv-1.2-1 libxext-dev
  libmono-system-runtime1.0-cil
The following packages will be REMOVED:
  acroread-escript libapr0 libflac++5c2 libmono-sharpzip0.6-cil
  libmono-system-runtime1.0-cil libsqlite0 libsvn0 libwavpack0 libwv-1.2-1
  libxext-dev x11proto-xext-dev
0 upgraded, 0 newly installed, 11 to remove and 6 not upgraded.
Need to get 0B of archives.
After unpacking 6881kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing acroread-escript (--remove):
 files list file for package `language-pack-gnome-en-base' contains empty filename
Errors were encountered while processing:
 acroread-escript
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Your help of course will be greatly appreciated. I've been trying to google this problem, but the results aren't turning up. I'd really like to get some work done! :)

Cheers

---

### Post by rickycodie on 2007-04-28
maybe you are trying to uninstall something that never got completely removedthe first time that you uninstalled it. also the bad upgradee is a bad thing most of the time ubuntu will just overwrite itself but it appears that this time it didn't . try to use this command
sudo apt-get beagle

it's for the beagle searcher. search you computer for above said files and delete them manually. that what i would try. it may or may not work, but it's my only thought.

oh, don't use beagle to delete your upgrade stuff.

---

### Post by iconoclasm on 2007-04-28
Well, instead of beagle (since I can't install or remove anything due to the broken packages), I ran:

```
locate acroread-escript
```

As that appears to be the one stopping autoremove from finishing. This is what turns up:

```
/var/lib/dpkg/info/acroread-escript.md5sums
/var/lib/dpkg/info/acroread-escript.list
/usr/share/doc/acroread-escript
/usr/share/doc/acroread-escript/plugins-description.html
/usr/share/doc/acroread-escript/copyright
/usr/share/doc/acroread-escript/LICREAD.TXT.gz
/usr/share/doc/acroread-escript/changelog.Debian.gz

```

Do you recommend I remove those manually?

---

### Post by iconoclasm on 2007-04-28
Actually, now that I think about it, any time I try to install or remove a package, it complains that 'language-pack-gnome-en-base' is pointing to an empty or missing file.

Maybe I just need to run a script to find out which file it's talking about? Or is there a tool to do that with apt?

---

### Post by iconoclasm on 2007-04-28
> **iconoclasm said:**
> Actually, now that I think about it, any time I try to install or remove a package, it complains that 'language-pack-gnome-en-base' is pointing to an empty or missing file.

Maybe I just need to run a script to find out which file it's talking about? Or is there a tool to do that with apt?

Well I ran the following script to check if any of the files in "language-pack-gnome-en-base.list" didn't actually exist. Turns out all the files in the list up to line 209 do actually exist as regular files.

Here's the script:
```

#!/usr/bin/perl -w

use strict;

my $file = '/var/lib/dpkg/info/language-pack-gnome-en-base.list';
my $i = 0;
my @lines;

open FILE, "< $file" or die "Can't open $file : $!";

while ( <FILE> )
{
    $i++;

    chomp;
    push @lines, $_;

    last if $i==209;
}

close FILE;

foreach (\@lines)
{
    next unless -f;
    next if -e;
    # if it's a regular file that exists, skip this pass
    # or else, contine and print the current line.
    # that one should be our 'missing' file apt is complaining about
    print "$_\n";
}

```

I even tried a "-z" test to see if there were zero-byte files. Runs clean, no results printed.

Maybe it's a file a dependency refers to that is empty/borked?

Any thoughts anyone?

---

### Post by iconoclasm on 2007-04-28
I can't figure it out. Am I going to have to re-install? :(

---

### Post by iconoclasm on 2007-05-01
I still haven't been able to figure out a fix for this problem.

I'd really like to avoid re-installing anything if possible. It's a broken package somewhere. Anyone know how to trace it down and fix the problem?

---

### Post by dcstar on 2007-05-01
> **iconoclasm said:**
> I still haven't been able to figure out a fix for this problem.

I'd really like to avoid re-installing anything if possible. It's a broken package somewhere. Anyone know how to trace it down and fix the problem?

So what does the Synaptic "Fix Broken Packages" function do?

---

