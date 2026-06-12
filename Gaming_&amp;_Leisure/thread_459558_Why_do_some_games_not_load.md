---
title: "Why do some games not load?"
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by Toadmund on 2007-05-30
I click on the game menu under applications for some games, these certain games, (kobo deluxe and nexuiz for instance) they start loading and then disappear.
Why are certain games doing this?
I don't think it's a graphics issue (ati xpress 200) because World of Padman works and a bunch of others, is it a dependency issue?

What is the issue here?

---

### Post by Lucifiel on 2007-05-30
Have you tried loading them from Terminal?

---

### Post by Toadmund on 2007-05-30
Um, what is the command to do that?

---

### Post by Lucifiel on 2007-05-30
Oh! Let me try and recall since I'm running Wolvix(my SATA hdd died and gonna be RMAed) and don't have Ubuntu right now. 

To use Terminal, you go to Applications====>Accessories====>Terminal.

As for how to run the games, go to erm, System and choose the first drop-down list(sorry don't remember what it;s called). Go to Main Menu(or was that called Menu?) and then, from the Main Menu window, you right-click on each game to get the commands for launching them. Once you have the commands, try copying and pasting them into Terminal.

---

### Post by Toadmund on 2007-05-31
Here is what I get for Kobo deluxe:
```
toad@toad-desktop:~$ kobodl
WARNING: Failed to get hardware screen surface.Switching to SINGLE buffer mode.
audio.c: Warning: Requested 512 samplebuffer, but got 940 samples.
Loading "Trance1"...
  Copyright (C) David Olofson, 2002.
.------------------------------------------------------
| MIDI File: /usr/share/games/kobo-deluxe/sfx/trance1.mid
|    Format: 0
|     Title: <Unknown>
|    Author: <Unknown>
|   Remarks: <None>
'------------------------------------------------------
  Done!
Loading "Test2"...
  Copyright (C) David Olofson, 2002.
.------------------------------------------------------
| MIDI File: /usr/share/games/kobo-deluxe/sfx/test2.mid
|    Format: 0
|     Title: <Unknown>
|    Author: <Unknown>
|   Remarks: <None>
'------------------------------------------------------
  Done!
Loading "Ballad1"...
  Copyright (C) David Olofson, 2002.
.------------------------------------------------------
| MIDI File: /usr/share/games/kobo-deluxe/sfx/ballad1.mid
|    Format: 0
|     Title: <Unknown>
|    Author: <Unknown>
|   Remarks: <None>
'------------------------------------------------------
  Done!
No hiscore entries found!
Segmentation fault
toad@toad-desktop:~$ 

```
:-k
Thanks for teaching me that though.:D

---

### Post by Scratty on 2007-08-31
I also get this. It used to work for me, but recently stopped working. I get the exact same thing. "No hiscore entries found!" followed by a segmentation fault.

I even tried to remove it and reinstall it. But alas, it was to no avail.

Anyone could shed some light on this issue?

---

### Post by Scratty on 2007-08-31
Ok..
```

kobodl -fullscreen

```
works (sometimes). There seems to be an issue with either the sound or the video-settings.
I'm still trying to work it out. I'm afraid there has been some update of feisty that broke kobo, because it worked perfectly for about two-three months ago or so, and now it doesn't. Reinstalling it doesn't fix it either.

---

### Post by Scratty on 2007-09-01
Ok. I've discovered that the following works consistently:
```

kobodl -nosound

```
apparently there seems to be an issue with the sound.

The weird thing is that I get errors that seems to be related to the graphics driver when I run w/o the -nosound flag:

```

  Done!
Name                     Score Start End
rasmus                       0    -1   0
X Error of failed request:  BadShmSeg (invalid shared segment parameter)
  Major opcode of failed request:  146 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Segment id in failed request:  0x1a0000f
  Serial number of failed request:  14813
  Current serial number in output stream:  14814
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x1a0000d
  Serial number of failed request:  119
  Current serial number in output stream:  124
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  79 (X_FreeColormap)
  Resource id in failed request:  0x1a0000c
  Serial number of failed request:  120
  Current serial number in output stream:  128

```

Anyone has any clues why this is so?

---

### Post by Scratty on 2007-09-01
Ok.. I think I've fixed it now. I have probably played with the sound settings a bit too much previously, and then I forgot about it. Playing around with the sound settings again fixed the problem. Seems ALSA didn't like my settings or something. These are the settings that works for me:
```

Yes
48kHz
50ms
Very High
 
100%
Yes
100%
50%
 
100%
Fast
High

```
It is very strange that this issue was interrelated with the graphics in some weird way.

Hope this info helps anyone out there having the same issue as me.

---

