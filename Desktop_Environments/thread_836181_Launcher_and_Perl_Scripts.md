---
title: "Launcher and Perl Scripts"
date: 2008-06-21
forum: Desktop Environments
---

### Post by petersra on 2008-06-21
Greetings,
Using Hardy and trying to use a Gnome launcher of a bash script.
In the script I call a perl script. Problem is that in CLI, script runs correctly.  When running via launcher, perl script does not execute.  

Execute permissions set in launcher.

shell script is:
#!/bin/bash
#
# Input file check.txt
# Output file check.csv
#
./checking.pl 
--------------------
and first few lines of checking.pl are:

#!/usr/bin/perl
$fname = "/home/rob/downloads/Checking2.csv";
$ofile = "check.csv";
use CSV;

open (IFILE,$fname) || die "Can't Open File: $fname\n";
open (OFILE,">$ofile") || die "Can't Open File: $ofile\n";

---

### Post by sdennie on 2008-06-21
You'll need to change your bash script to give the absolute path of the perl script.  Using the relative path "./" isn't always going to work.

---

