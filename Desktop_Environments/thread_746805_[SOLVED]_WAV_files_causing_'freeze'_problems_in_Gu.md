---
title: "[SOLVED] WAV files causing 'freeze' problems in Gutsy / Gnome"
date: 2008-04-05
forum: Desktop Environments
---

### Post by CRISM on 2008-04-05
I recently installed Gutsy Gibbon on an AMD 64 dual processor system.

Normally, moving my mouse pointer over a file causes the file to be high-lighted, and then I can click on it for access. However, when I move my pointer over a .wav file, it won't high-light. Further, I can no longer access that file or any other file in the folder with my mouse, even the ones I could previously access. It's as though the files are 'frozen'. None of the files are high-lighted any more, and I cannot access any of them by clicking. (Note that I have not even clicked on the .wav file, just moved the pointer near it for this to happen.)  If I then wait a minute or so, everything seems to go back to normal, and I can access files again...that is until I approach the wav file, at which point things 'freeze' again. This behavior is not restricted to just one wav file, but is common to all wav files on my system. I haven't tried other sound file formats, but so far the wav file is the only type of file where this behavior is observed. 

Meanwhile, access to things through the terminal window does not seem to be affected. I can access sound files, move them, copy, play, anything I want as long as I'm using the command line. I know the files themselves are fine. Anyone have any suggestions? Thanks.

P.S. I also discovered that this only happens when icons are displayed. If I display items by list, everything is fine.

---

### Post by CRISM on 2008-04-10
Never mind. I found a 'work-around' solution here:
[http://ubuntuforums.org/showthread.php?t=652913](http://ubuntuforums.org/showthread.php?t=652913)
You have to turn off the preview option for sound files. After that, things are back to normal. Apparently this feature has problems on some systems.

---

