---
title: "How can I change location of desktop icons ?"
date: 2009-08-06
forum: Desktop Environments
---

### Post by vaerer on 2009-08-06
How is it possible to change the position of multiple desktop icons ?

In windows you drag a selection box around a group of icons then when they are selected you drag them to their new location. The relative position of each icon to the other icons within the selection you are moving stays the same.

In Xubuntu when I try to move a group of icons it only moves one of the icons. Which makes me wonder what's the point of being able to select more than one icon if you can't move them together? :confused:

---

### Post by quixote on 2009-08-07
I'm not that familiar with xfce, but the icons-move-together behavior you describe is how it works in gnome.  Are you sure you don't have some prefernce setting set in a way that produces that bizarre behavior?  In gnome, some of the Desktop behavior is determined by the Preferences under "Edit" in Nautilus.  (I know.  It doesn't make any sense to me either.  :) )

---

### Post by vaerer on 2009-08-08
I've looked through all of the related and semi-related settings pages and not been able to find anything about it.  It would be good to know if it's the default under Xubuntu or if I've just accidentally set it up this way.

---

### Post by JoeNZ on 2009-08-08
I have been using Xubuntu for a month or so and I am afraid that is how it is - 1 at a time. You cannot right-click and 'auto arrange' either so I suppose dragging the icons around is how it is done.

---

### Post by fieroboom on 2009-09-15
Hey guys, I keep seeing this thread pop up occasionally, and one user wrote a perl script for it, but it was more of his/her own quick-n-dirty, so I thought I'd bust one out with some in-depth comments in case you want to use it. This script will just automatically arrange the icons starting in the upper left, in no particular order, except that 'Home', 'File System', and 'Trash' will be the first 3 icons down the left-hand side.
If you'd like some changes, such as order by type, alphabetically, etc, just let me know, and I'll be happy to make the changes (or you can play with it and pick up a very important tool - Perl... ;o)
Anyway, here it is:
```

#!/usr/bin/perl

######################################################
## Script to automatically arrange desktop icons, starting in the upper left. This can be run hourly from crontab like so:
## 0 *     * * *   <username>    /usr/local/bin/icon_arrange.pl
## And/Or it can be placed in rc.local to run on every reboot. I don't reboot my machine very often, to I use the crontab option.
######################################################

use strict;
use File::Copy;

## might be multiple users, find out who's using the current x-session-manager
my @user = `ps aux|egrep 'x-session-manager'|grep -v egrep`;
chomp(@user[0]);
@user[0] =~ s/^(\w+)\s.*?$/$1/g;
my $user = @user[0];

## find out the location of the file (helps across distributions/updated kernels, etc...)
my $icons_file = `locate icons|grep desktop|grep screen0`;
chomp($icons_file);

## just in case there are multiple users, set the /home/<user>/ to the $user variable:
$icons_file =~ s/^\/home\/\w+\//\/home\/$user\//g;

## finally, we now have the right file, make a backup & proceed with parsing it:
copy("$icons_file", "$icons_file.bak");

open(CONFIG, "<$icons_file") or die("Can't open $icons_file for reading!!");
my @icon_config = <CONFIG>;
close(CONFIG);

## grab all the icon names on the desktop. Don't care about their positions, since I'm giving them new ones:
my @icons;
foreach my $line (@icon_config) {
	if ($line =~ /^(\[.*?\])$/) { push(@icons, $1) }
}

## open the new config file to write to it:
open(NEWCONFIG, ">$icons_file") or die("Can't open $icons_file for writing!!");

## I personally prefer 'Home' at the top left, then 'File System' underneath it, then 'Trash', then so on...
print NEWCONFIG "[Home]\nrow=0\ncol=0\n
[File System]\nrow=1\ncol=0\n
[Trash]\nrow=2\ncol=0\n\n";

my $row_count = 3;
my $col_count = 0;

foreach my $icon (@icons) {
## on my particular desktop (1280x2048 dual monitor) there are 9 rows... Not sure how this plays out for lower resolutions...
## so here I incremement the row count on each loop until it reaches 9, then reset it to 0 and increment the col count up 1:
	if ($row_count > 9) { $row_count = 0; $col_count++ }
	if ($icon !~ /^(\[Home\]|\[File System\]|\[Trash\])$/) { print NEWCONFIG "$icon\nrow=$row_count\ncol=$col_count\n\n"; }
	$row_count++;
}

```

Download: [http://grandesigns.net/icon_arrange.pl](http://grandesigns.net/icon_arrange.pl)

Have fun! :D
-Paul

---

