---
title: "Desktop icons auto-arrange?"
date: 2005-07-18
forum: Desktop Environments
---

### Post by amohanty on 2005-07-18
Hi,

One of my pet peeves with the desktop is that I cannot set it to autoarrange (kind of like cleanup, just automatic). As a result sometimes, some of my icons are rendered on top of one another, especially when I have some remote smbfs drives mounted, or I pop in a CD.

Is there any way to set it up so that new icons automatically go in the right place, ie bottom of the list for eg.?

Thanks

AM

---

### Post by 4m2mohan on 2005-09-25
I am also Need help in this Topic.

I can't Auto Arrange Icons how can i do that

---

### Post by NeoChaosX on 2005-09-25
Right-click on the desktop, and select "Keep Aligned". That's how you can auto-arrange.

---

### Post by pmj on 2005-09-25
[QUOTE=NeoChaosX]Right-click on the desktop, and select "Keep Aligned". That's how you can auto-arrange.[/QUOTE]
I hope there's a way to get actual auto arranging of icons, because Keep Aligned only makes icons sort of snap to grid. It doesn't prevent them from appearing on top of each other.

---

### Post by critofur on 2007-09-02
Also needing this feature but can't find where/how to turn it on???

---

### Post by kaushis on 2007-09-03
im looking for this tip too!

---

### Post by BlackMeTaL on 2007-09-03
I know KDE has this, but I don't know about Gnome. If there is high demand I can write a script for it, let me know.

---

### Post by heat84 on 2007-11-29
Still no way to do this yet?:( There's not Ubuntu programmer that's obsessive compulsive? I guess that would explain why I apparently have no aptitude for programming.

---

### Post by meindian523 on 2007-11-29
@BlackMeTal

There IS high demand,write that script please....

---

### Post by mikawber on 2008-01-07
I would really love to have this feature too. help us out someone

---

### Post by p1977p on 2008-03-11
check out the [COLOR=DarkRed]**'~/.config/xfce/desktop/icons.screen0.rc'**[/COLOR] file. (the actual name may vary depending on the desktop manager you use).

 This file lists the positions of various icons that were displayed recently.
I modified this file to display the Standard icons (like home,trash, filesystem,etc) at specified places, and other icons like CD-ROm drive or Flash drive at other fixed places (say, along the right hand side of the screen). Other file/folder icons are automatically placed at other locations on the screen and do not interfere with these icons.

_P.S_.: these icon names should be at the top of this file. ( I guess the entries are parsed from top to bottom)

The file should automatically be updated each time the user logs off, so that unnecessary items are removed, but apparently, this doesn't happen. Can someone write a script for the same?

---

### Post by PGScooter on 2008-03-27
I am still looking for a solution to this.. not a big deal, but I think that it wouldn't be too hard to implement. any ideas?

---

### Post by ballas on 2008-05-19
Hmm.. I wonder why it's not by default, the auto-arrange? In any case, has someone already found a solution ?

Regards! :)

---

### Post by PGScooter on 2008-06-29
has this been added in later releases or is this still a problem?

If there is still demand for this, I will write a script (in perl). I am not an accomplished programmer, but I do not think that it would take me too long.

Let me know

---

### Post by meindian523 on 2008-06-30
it has not been added(yet).

---

### Post by PGScooter on 2008-07-02
well, here's what I have so far. It has many potential problems, but it works for me. If there is any demand, I could clean up the code, make it customizable (if you want the trash to always be in a certain spot, etc), and maybe do different kinds of sorting. I should probably have added more comments.

any suggestions on the coding are welcome.

I hope someone gets some use out of it :)

```

#make sure you change 'user' on line 4 to the username of the desktop you want to organize
use strict;
use warnings;
my $conffile='/home/user/.config/xfce4/desktop/icons.screen0.rc';
open(CONF,"$conffile") or die "can't find the config file";
my $all;
while (<CONF>) {
	$all=$all.$_;
}
my @oldnames=($all=~/\[(.*)\]/g);
my @allnames=sort { lc($a) cmp lc($b) } @oldnames;
print "testing sort:";
print join("\n",@allnames);
my @rows=($all=~/row=(\d*)/g);
print join("\n",@allnames);
print "ok now I will print the amount of rolls\n\n\n";
@rows=sort(@rows);
my $maxrow=$rows[-1];
print "the max rows is $maxrow";
my $numicons=scalar(@allnames);
print "number of icons is $numicons";
my @cols=($all=~/col=(\d*)/g);
@cols=sort(@cols);
my $maxcol=$cols[-1];
print "the max cols is $maxcol";
my $i=0;
open(OUTPUT,'>icons.screen0.rc');
for (my $j=0;$j<=$maxcol;$j++) {	
	if ($i<=19) {
		for (my $k=0;$k<=$maxrow;$k++) {
			print OUTPUT "\[$allnames[$i]\]\nrow=$k\ncol=$j\n\n";
			$i++;
		}
	}
}
close(OUTPUT);

```

---

### Post by PCFascist on 2008-07-21
Sorry PGScooter, could you let us know how to use this code?


[QUOTE=PGScooter;5303197]well, here's what I have so far. It has many potential problems, but it works for me. If there is any demand, I could clean up the code, make it customizable (if you want the trash to always be in a certain spot, etc), and maybe do different kinds of sorting. I should probably have added more comments.

any suggestions on the coding are welcome.

I hope someone gets some use out of it :)

---

