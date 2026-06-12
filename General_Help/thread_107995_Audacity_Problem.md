---
title: "Audacity Problem"
date: 2005-12-24
forum: General Help
---

### Post by greymaus on 2005-12-24
I've installed Audacity in my Linux box. No problems installing; went very smoothly.  HOWEVER...As soon as I invoke the program, I get this: 

"There was an error initializing the audio I/O layer.  You will not be able to play or record audio."  

If I press the red RECORD button, I get this:

"Error while opening sound device. Please check the input device settings and the project sample rate."

When I try to specify audio input and output devices, the dialogue boxes to do that are blanked out and will accept no input.

I also run XMMS, since all my music selections are in MP3 format.  XMMS has no problems with audio input or output devices.  I don't know what to make of all this. Suggestions, anyone?

(I also run Audacity under Windows XP, where it works perfectly.)

---

### Post by jasondean on 2005-12-25
Hello, I had the same problem.  I run KDE and what solved the problem was to run```
 artsdsp audacity
```

This might also help.

[http://audacityteam.org/wiki/index.pl?LinuxIssues](http://audacityteam.org/wiki/index.pl?LinuxIssues)

---

### Post by Zalbor on 2005-12-25
The way I've found to "solve" this (I read it here, actually) is to go to System->Preferences->Sound and disable sound before running audacity.

---

### Post by jbmalone on 2005-12-25
Or close XMMS.  I had that error with mplayer, and when I closed XMMS it went away.

---

### Post by greymaus on 2005-12-26
To all who've responded:  Tried all your suggestions.  Nothing worked.  Still unable to record or playback in Audacity.

 A sound editor utility that won't record or playback is of very little use.  Looking for a good replacement.

---

### Post by greymaus on 2005-12-26
Status report, Audacity problem:
The Audacity editor is now up and running successfully, after days of hair-tearing frustration--and it's a testament to my muddle-headedness that the solution was so simple.

The source selector (CDROM, VIDEO, etc) was mis-set.  I hadn't noticed that it was set for "Line 1" when it needs to be set to "Line". And I'm an ex-communications specialist?

Gad.

DOUBLE-CHECK THE SMALL STUFF, FOLKS!! [[gg]]

---

