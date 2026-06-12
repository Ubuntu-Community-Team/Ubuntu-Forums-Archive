---
title: "bygfoot-update problem"
date: 2008-04-10
forum: Gaming &amp; Leisure
---

### Post by boywholinuxed on 2008-04-10
hi
i am new to linux and i installed bygfoot-2.01.i read somewhere if u type bygfoot-update then you can get the real names of teams and players,but when i did that the following  came:
jithin@mypc:~$ bygfoot-update

bygfoot-update: A bash script keeping your Bygfoot Football Manager up-to-date.
Version 2.0.1.
See the file UPDATE for some more information.
Call bygfoot-update -h|--help for usage information.


** b-u: checking for sed... ok
** b-u: checking for tar... ok
** b-u: checking for bzip2... ok
** b-u: checking for wget... ok
** b-u: checking for patch... ok
** b-u: checking for cvs... failed

** WARNING: Didn't find working cvs, maybe it's not in your PATH.
** WARNING: You might not be able to use all bygfoot-update features.

then i press enter
and the following comes:** b-u: checking for zenity... 2.20.0 found.
and a window pops out and  i select option 2.

and i press enter in the screen that follows it

and then i check the terminal and the following error comes

ed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
sed: can't read england/league*.xml: No such file or directory
.....
there were many more errors of the same type followed by this:
removed `team_belgium_charleroi.tar.bz2'
Country directory belgium not found.
removed `team_belgium_club.tar.bz2'
Country directory belgium not found.
removed `team_belgium_gba.tar.bz2'
Country directory belgium not found.
removed `team_belgium_genk.tar.bz2'
Country directory belgium not found.
removed `team_belgium_gent.tar.bz2'
Country directory belgium not found.
removed `team_belgium_lierse.tar.bz2'
Country directory belgium not found.
removed `team_belgium_lokeren.tar.bz2'
Country directory belgium not found.
removed `team_belgium_standard.tar.bz2'
Country directory belgium not found.
tar: team_england_ipswich.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
i dont understand what to do update the players and team name to real name because the current names are so confusing!

so please help me!!!!

---

### Post by tlocke on 2008-05-18
It can't find the files to update because the directory is incorrect.
It needs to be 

$HOME/.bygfoot/definitions

not 

$HOME/.bygfoot/


Regards,

---

