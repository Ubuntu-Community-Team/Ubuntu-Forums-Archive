---
title: "bluetooth script"
date: 2006-07-06
forum: Desktop Environments
---

### Post by binarymelon on 2006-07-06
I made the following script by modifying a flickr upload script I think.  It doesn't seem to work for files on the Desktop.  I'm just wondering if someone could give me some hints as to why and how to fix it.

```
#!/usr/bin/perl -w

use strict;

(my $me = $0) =~ s|.*/(.*)|$1|;


my $false = 0;
my $true = 1;

my $file;
my $filenum;
my $random_file;

# set up loop to go through files passed to script
# rotate each script, increment the file number, and then update the status
# for now, assume that they are all jpegs, and do not put up a warning

$filenum = 0;

my @filelist;

# test for argv as Nautilus could just use URI's
if (@ARGV) {
    @filelist=@ARGV;
} else {
    #extract files from NAUTILUS_SCRIPT_SELECTED_URIS
    @filelist = split ("\n", $ENV{NAUTILUS_SCRIPT_SELECTED_URIS} );
}

foreach $file (@filelist) {
    $file =~ s|^file://||; # drop any file://
    ++$filenum;

    system("gnome-obex-send $file");

}

exit( 0 );

```

---

### Post by binarymelon on 2006-07-19
bump

---

