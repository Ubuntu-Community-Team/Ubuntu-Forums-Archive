---
title: "AmaroK not workin- no sound =playlist finished"
date: 2006-06-28
forum: Desktop Environments
---

### Post by thedevnull on 2006-06-28
Hello Everyone,

  I have read all the docs and done exactly as was said in the Wiki and the help pages but am still having the same problem.  I am running Kubuntu 606 with Amarok 1.39 with the libxine and w32 codecs installed.  Also I am patched and updated as of today.  I have it set to xine engine with the plugin set to auto.

I have followed the instructions here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and have the libxine and w32 codecs installed.  

In amarok when I open a file it just says PLAYLIST FINISHED and that is it.  It never plays a file.  All other players VLC/Codeine/etc. work just fine and have no issues.  

Any ideas??  Any help is appreciated. =)

---

### Post by yage on 2006-06-28
Try starting amarok from a terminal... if you get errormessages post them here.

---

### Post by Jucato on 2006-06-28
which libxine did you install? Just checking to make sure it's *libxine-extracodecs*.

Also what type of audio were you trying to play? Can you play OGG's? There's a sample OGG music file in /usr/share/example-content that you could use to test Amarok.

---

### Post by thedevnull on 2006-07-05
Hello,

  I get the following errors when I start Amarok on the command line:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
ScimInputContextPlugin()

Any ideas?

---

