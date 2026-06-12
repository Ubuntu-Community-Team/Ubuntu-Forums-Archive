---
title: "GearHead Arena and GearHead 2 on Ubuntu"
date: 2008-08-11
forum: Gaming &amp; Leisure
---

### Post by daemonward on 2008-08-11
I found some great open source 3D isometric role-playing games!

The latest graphical SDL versions of GearHead:Arena and GearHead 2 for linux can be downloaded from:

[http://michalis.ii.uni.wroc.pl/~michalis/gearhead_unix/](http://michalis.ii.uni.wroc.pl/~michalis/gearhead_unix/)

GearHead:Arena looks and plays great:

1. Extract the archive
2. Enter the GearHead directory
3. Double click the 'arena' binary to play. No compiling required.

I highly recommend creating an 'arena.cfg' text file and adding the lines for FULLSCREEN, MINIMAPON, and NAMESON to get the best experience.:)

Why do they only have the text based version in the Ubuntu repos!? The SDL version should definitely get added to Universe!:guitar:

Unfortunately, I still can't get GearHead 2 to work. At first, all I could see was a blue screen. After uncommenting the REVERT_SLOWER_SAFER line in 'gearhead.cfg'(which gets created the first time you run the 'gearhead' binary) the splash screens, start menus, and character creation started working. But the game crashes whenever I try to start the 'RPG Campaign'. Granted, this game is only version 0.503. But still...:(

Running GearHead 2 from the console, I get this error message after it crashes:

An unhandled exception occurred at $A3A6001C :
EInvalidOp : Invalid floating point operation
  $A3A6001C
  $B70910BD
  $B7094E7E
  $B704B716
  $B715DCA1
  $B7173DB3
  $B7174014
  $B716765D
  $B7167843
  $B701EAF0
  $B66C5942
  $B66C66FE
  $B66BBF18
  $B66D74DE
  $B661D762
  $B66204F7
  $B66209A5


I am running Ubuntu 'Hardy Heron' 8.04.1 32-bit.

---

