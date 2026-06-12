---
title: "Stitching together multiple .flv files"
date: 2009-02-12
forum: General Help
---

### Post by t0p on 2009-02-12
I have a number of short .flv files which I want to join together.  Unfortunately, the **cat** command doesn't concatenate the files into an effective video file.

How can I do this?

---

### Post by mb_webguy on 2009-02-12
Video files aren't fancy text files.  You can't just tape them together end to end and expect them to work as one long file.  You'll need to use a video editor.  Avidemux is the simplest general purpose editor you'll find, and is more than sufficient to do what you want.  And it supports flv files, which is good since you won't have to do any conversion.

Install Avidemux using Add/Remove Applications, Synaptic, or in the terminal using the command "sudo apt-get install avidemux".  To do what you're asking, follow the following steps.

1) Open the first flv file in Avidemux.  
2) At the bottom, click the "Selection: start" button (the one with the "A").  
3) Move the slider to the end of the video, and click the "Selection: end" button (the one with the "B").
4) Go to Edit->Copy to copy the selection.  
5) Open the next flv file.  The slider should be at the beginning of the video.  
6) Go to Edit->Paste to paste the video you previously copied to the beginning of the second video.  
7) Repeat steps 2 through 6 until you've reached the last flv file.
8) Make sure the video and audio selects on the left are set to "Copy", and the format select is set to "FLV".  Click "Save", give your new video a name, and click "Ok" to save the video.

---

### Post by t0p on 2009-02-13
Thanks for the tip about avidemux.  But the steps you outlined didn't work - every time I **opened** a new file, the one I'd copied before just vanished from avidemux.  I worked out what I needed to do was use the **Append** function (located in the File menu).  So, I *open*ed 1.flv.  I used the "A" and "B" buttons to mark its beginning and end.  Then I *append*ed 2.flv, and used "A" and "B" to mark the beginning and end of the entire selection... then *append*ed 3.flv and so on.

Anyway, thanks for pointing me in the direction of avidemux.

---

### Post by mb_webguy on 2009-02-13
Every time you open a new file, it will replace the old one, *but the section you copied will remain in the Avidemux clipboard*.  Once you've copied a section of a file (or the whole file) it will remain available to be pasted into a new file until you copy something else or close Avidemux.  I've done exactly what you're talking about exactly the way I described it several times before when I've had a video file split into multiple parts which I wanted to splice together.

Doing it the way I suggested gives you more flexibility than with Append, since you can chose exactly what you add together, such as if you want to leave off black frames or credits.

---

### Post by t0p on 2009-02-13
> **mb_webguy said:**
> 
Doing it the way I suggested gives you more flexibility than with Append, since you can chose exactly what you add together, such as if you want to leave off black frames or credits.

Okay, I'll explore this more next time I need to join together some vid files.

---

