---
title: "amaroK and cues"
date: 2006-10-10
forum: Desktop Environments
---

### Post by The Keeper on 2006-10-10
I've got a bunch of FLACs and each contain multiple tracks, I also have cue files for the files. I can play them in Windows using foobar2000, and according to amaroK changelog cue files have been supported since version 1.3. Call me stupid but I haven't found any way to use cue files with amaroK, what's the trick? Trying to open the cue files directly only results in the "Some media could not be loaded" error".

---

### Post by Mr Frosti on 2006-10-10
In Amarok, try loading the cue file by going to the Playlist view and then dragging the file into the main window. If this doesn't work, try renaming the cue file to <filename>.pls

This will force Amarok to read the cue file as a playlist, which you can then edit the track orderings for. You can save this as "Playlist -> Save Playlist as".

I hope this is what you are describing.

---

### Post by The Keeper on 2006-10-11
Dragging the cue file into playlist didn't work, same error as earlier. Renaming cue to pls didn't help either. :(

---

### Post by The Keeper on 2006-10-12
Well, I think I figured it out. I noticed that in foobar2000 you can embed CUE-sheets into FLACs themselves. I then tried to play one of the FLACs in AmaroK and noticed that while each track won't appear on playlist, track names change over time. It's a pity that CUE support is this limited but at least this is better than nothing.

---

