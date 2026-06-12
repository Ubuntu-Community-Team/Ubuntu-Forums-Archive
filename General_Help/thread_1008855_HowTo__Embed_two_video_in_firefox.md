---
title: "HowTo : Embed two video in firefox ?"
date: 2008-12-11
forum: General Help
---

### Post by ekkawit on 2008-12-11
How can I use EMBED tag (html) to run two video in firefox or other browser on Ubuntu.

I try VLC, MPLAYER. But it cannot use ATTRIBUTE "Volume" PARAMETER to make sound volume adjustment.

If anyone know how to prove it, plaese reply this thread.

Kind Regards
Ekkawit Puinongpo
System Engineer

---

### Post by fragos on 2008-12-12
Thanks to Microsoft the issue of using EMBED or OBJECT becomes very confusing and depends on which browser is being used to view the video. The best solution I've found is to this javascript method from Google -- It works the same regardless of browser. 

[http://code.google.com/p/swfobject/](http://code.google.com/p/swfobject/)

---

### Post by ekkawit on 2008-12-15
> **fragos said:**
> Thanks to Microsoft the issue of using EMBED or OBJECT becomes very confusing and depends on which browser is being used to view the video. The best solution I've found is to this javascript method from Google -- It works the same regardless of browser. 

[http://code.google.com/p/swfobject/](http://code.google.com/p/swfobject/)

Thanks. Let's me try. And if it work, I will feedback in this forum.

---

### Post by ekkawit on 2008-12-18
SWFObject cannot use to play VIDEO file.
Or someone can ? please tell me how to.

---

### Post by PocketDog on 2008-12-18
Off the top of my head ```
<embed src="http://path/to/video.mpg" autoplay="true" volume="100"/>anything you like goes here</embed>
``` will embed any type of file. Change .mpg (obviously) to suit

---

### Post by ekkawit on 2008-12-18
To PocketDog

Your code can embed video file.
But why VOLUME parameter cannot use.
I set volume=0 ,It still have sound.
If you know how to set VOLUME for video embed, Please tell me.

Thanks in advance

---

### Post by PocketDog on 2008-12-18
The volume attribute works for some players but not others. You don't have much control at all really. It's better to adjust the volume of the video itself with an editor if you have access to the file

---

