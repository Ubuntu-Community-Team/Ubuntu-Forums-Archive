---
title: "cleaning linux."
date: 2006-01-12
forum: Desktop Environments
---

### Post by M3lted on 2006-01-12
hey .
I was wondering .
When u use xp , u need to keep it clean from time to time .
Like the register , temp folder ,prefetch folder ,defragging once a while and some other stuff.
Now im still very new to linux in general and im quite curious what u do in linux ,to keep it run smooth, and to keep it clean .
Does any one got some info or some links for me where i can read up on that subject. ?

thanks in advance :)

---

### Post by Thirsteh on 2006-01-12
You do nothing. Linux does not need regular maintenance such as defragmentation et cetera. It's one of the things I love about Linux.

---

### Post by M3lted on 2006-01-12
u kidding me rite? :)

---

### Post by Thirsteh on 2006-01-12
Absolutely not. No temporary or fragmented files will slow your computer down with time in Linux. All your applications' profiles are stored in your home folder with a '.' prefix which means they're hidden usually. You can open a terminal in your home folder and type 'ls -la' to see these. These are the only things that "clutter up" your drive, they do this instead of using the registration database in Windows --- and usually they're not big so not worth cleansing them.

---

### Post by byen on 2006-01-12
not really a great tip...but incase you were interested ...you can clean up the temporary dir where all your installation files (when u use apt-install) are stored by typing this code in the terminal:
sudo apt-get clean

But as stated above...everything is taken care of by the OS here. Infact you do not even have to do the apt-get clean process as it takes care of that too...

No. He isnt kidding..isnt Linux wonderful ;-)

---

### Post by Thirsteh on 2006-01-12
;) Viva la Linux! Or something.

---

### Post by M3lted on 2006-01-12
Well that quite nice to know , i mean i spend lots of time fixing and cleaning people's pc :confused:  , and infact al what they should do is use linux :)
its so much better.

Lol next time if i get asked to fix a windws pc im gonna install linux on it ;)

---

### Post by leech on 2006-01-12
[QUOTE=M3lted]u kidding me rite? :)[/QUOTE]

Nope, the Linux distributions aren't stupid and don't have a huge registry that gets cluttered with a bunch of useless crap.  Think of all the information the registry in windows contains; User settings, file associations, serial keys, trial expirations, keys which you touch and you have to re-install.

The only thing the Linux desktops keep are hidden files as someone else already stated.  The closest thing to a registry that Gnome has is gconf, but it is very clean and only hides some of the options that most people don't need to change on a regular basis.  File associations are handled by Nautilus.  Since all the software that comes wth the distribution is free, no need for serial keys or for trial experation stuff.  Most importantly, there are no keys in gconf that will destroy your system.  If for some reason you have set something in gconf that makes it so you can't log into gnome, you can just reset it by 'rm -r ~/.gconf' and 'rm ~/.gconfd' and all the default settings will be reset.

Leech

---

### Post by M3lted on 2006-01-12
Well, Im kinda amazed.
If linux in general handles thing so well , Its just stupid that so many ppl still use windows Imo
I mean so many user's cleaning defragging scanning its just so much time together ,and that time could have been used so much more usefull insted of keeping trying to keep your oss clean lol :)

---

### Post by Azriphale on 2006-01-12
A) Linux has no registry or equivalent, nothing to do there.
B) The /tmp folder gets cleared on every boot
C) Linux filesystems are genreally very resilient to fragmentation because of the way it determines where to write files stuff.

As for clearing apt's cached .debs, you don't need to unless you need the harddrive space. In my experience (much to my irritation, in fact), apt clears this on occaision when it decides that its getting too big (I think it was in the region of 600MB when it was clearing mine). As I say, no need to "sudo apt-get clean" because of point (C) above, unless you need the disk space.

Its a zero waste-of-time-maintenance OS :)

And installing Linux on it is the best way to fix it, as you say....

---

### Post by M3lted on 2006-01-12
Oke thanks guy's/girl's , for the fast info :)

---

### Post by Thirsteh on 2006-01-12
Just ask ;)

---

### Post by gnuconvert on 2006-01-14
Although I'm a newbie to Linux, I have read that Linux does bad things if you run out of disk space. It would seem then that just checking periodically to see that you haven't filled up your hard disk (root partition) to the max would be the only "cleaning" that's needed. Other than, of course, keeping big bad bloated windows operating systems off your PC! ;)

---

### Post by beow on 2006-01-14
Actually also in linux you can clog your system by copying files and directories to new locations etc.

A good tool to keep your file system clean is to use the "fslint" program:

$ sudo apt-get install fslint

and it winds up in your "System tools" menu. Try it, it's easy to use.

---

### Post by Mustard on 2006-01-14
[QUOTE=beow]Actually also in linux you can clog your system by copying files and directories to new locations etc.

A good tool to keep your file system clean is to use the "fslint" program:

$ sudo apt-get install fslint

and it winds up in your "System tools" menu. Try it, it's easy to use.[/QUOTE]

I can't find this package.  Have you spelt it correctly?

I'm pretty sure its not in the repositories.

Here is a link to it at Freshmeat...

[http://freshmeat.net/projects/fslint/](http://freshmeat.net/projects/fslint/)

---

### Post by galgoz on 2006-01-15
So if you install program A and then install programs B - Z and then decide to take program A off of your computer you arent' going to cause fragmentation when the space that A was occuping get partially useb by program AA that is bigger than the hole created by removing program A?  Seems like fragmentation is something that would still be I problem to me, but what do I know?

---

### Post by briancurtin on 2006-01-15
fragmentation still does occur, but it is not nearly the problem that it is in windows.

---

### Post by beow on 2006-01-20
Sorry, you're right. I downloaded fslint rpm package from 
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)
and installed with alien:

sudo alien -i fslint-2.12-1.noarch.rpm

worked fine

---

### Post by ice60 on 2006-01-20
hi, i just installed FSlint, i had been trying to install kleansweep but i'll use this instead :) 

when i click on find it finds 1000s of things in my themes and icons' folders which i want to exclude from the search, do you know how to do that? i have added them to the "Paths to exclude" but it hasn't worked, can you help? thanks.

---

### Post by beow on 2006-01-21
From the picture you included it seems like you're excluding 
/.icons
which is not correct. Either use the full path:
/home/iceni60/.icons
or the short form:
~/.icons

/.icons referes to a directory directly under the root that (probably) not exists. The same goes for /.themes

Good luck!

---

### Post by ice60 on 2006-01-21
thanks, beow. it's works :D  i'm not sure if i would have worked it out in the end or not :confused: either way i'm hoping this program will make me more familiar with the file system. it seems deleting duplicates is similar to deleting dups in windows - don't do it unless you know what you're doing!

i just realised why i made the mistake; when i editted in the paths, i thought FSlint was in my home directory, but it was the editor loading into my home directory which made me think the program was already there.

---

### Post by gabhla on 2006-01-21
Wow...thanks.  It works great for me.

---

