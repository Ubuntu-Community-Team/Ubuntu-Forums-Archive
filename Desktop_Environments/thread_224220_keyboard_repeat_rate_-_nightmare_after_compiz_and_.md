---
title: "keyboard repeat rate - nightmare after compiz and xgl"
date: 2006-07-27
forum: Desktop Environments
---

### Post by jezjones on 2006-07-27
Hi everyone,

So i managed to get the whole xgl desktop working and it is pretty good, very few problems.

Since then though my keyboard repeat rate has been almost unusable, certainly requiring many re-types when i find keystrokes are getting ignored... as you can imagine password fields can take some time.

Now i know that the settings for this are in gconf-editor...
in desktop - gnome - peripherals - keyboard.
default is delay=500 and repeat=30

I have tried setting he delay as low as 200 and the repeat down to 10 ... a every increment inbetween.

I cant seem to find any explanation of what these figures are.. or more importantly whether i should be going up or down and by single numbers or hundreds.
I recently put Suse 10.1 on another partition, which is using the xgl desktop and had a look in there, which is where i found the default numbers above... these do match the default in Ubuntu aswell (i think from memory).

I have managed to type this, but it has taken alot of re-writes.

My question is what are these numbers?
How can i find out what the right numbers are?

Any suggestions would be great... and more documentation on gconf-editor would be really good... for a start should i sudo gconf.. or run it as my normal user account?

THanks

JEz

---

### Post by jezjones on 2006-07-28
More info....


I have been searching and i think i have found some info....

On the redhat site it talks of a tool in gnome to set the repeat and delay rate.. i am guessing that this is a front end to these numbers in gconf

There it says the delay is the number of milliseconds before it repeats and the rate is number of characters a minute .. i'll try some things with this in mind when i get home.

ALSO, sudo gconf, will do system wide settings and without will be for individual user.

I hope this helps someone... although if anyone knows of a decent bit of documentation for the stuff in gconf it would be really useful...

THanks

jez

---

### Post by jezjones on 2006-07-31
SOLVED I THINK!

So further to the info above about the tool in the gnome-control centre, which i got to through the Debian menus !! (cant find it in the default Ubuntu menus).
I found this tool for setting the speed and repeat rate. After some trial and error with slide settings and the test box, i have managed to get the repeat rate to a workable setting.

Returning to gconf-editor to see what numbers were in there, i found that the delay is now 878 and the rate is still 30.

I hope this helps someone else.
BTW, if you dont have the Debian menus google these forums for it, i cant remember exactly how i turned them on, could have been Automatix.

Jez

---

