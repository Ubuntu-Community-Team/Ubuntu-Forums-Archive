---
title: "Big problems occur when enabling Beryl"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by TS28 on 2007-06-03
Hello!

After getting Beryl running, some big problems occured, interestingly, the same problems as I mentioned in my other thread [here]("http://ubuntuforums.org/showthread.php?t=463123")

Basically, I can not minimize windows without right clicking and telling it to do so on the bottom bar, and the bars on specific windows which would normally let me do so, are gone.

I am also unable to move windows, minimize, etc.

I made a screen shot in an attempt to make things more easy to understand in case I did not do a good job at explaining.

[IMG]http://img.photobucket.com/albums/v486/TS28/Berylproblem.png[/IMG]

Thanks again! :)

---

### Post by Kuoi on 2007-06-03
Look for my reply at this treath : [http://ubuntuforums.org/showthread.php?t=458744]("http://ubuntuforums.org/showthread.php?t=458744")

Hope it helps , Kuoi

---

### Post by zero244 on 2007-06-03
I had the same problem I added this line to the bottom of the screen section in the xorg file.
Option "AddARGBGLXVisuals" "True"
That fixed the problem for me.
I would try turning on Window Decoration in beryl settings manager too.
Beryl is great fun.........but for many people its a nightmare to get running right and keep running right.
Right now all I can use is Window shadows......thats it..........nothing else nothing.
Im not sure how long even this is going to work.
Fortunately Ubuntu responds well to reseting your computer. I think if I reset my Windows machine this much it would definately get some corrupt files.
Good Luck.

---

### Post by TS28 on 2007-06-03
Worked like a charm, Kuoi, many thanks :)

You people are amazing.

---

### Post by Kuoi on 2007-06-03
No thanks , glad I could help with this issue again.

It seems these settings and configuration fixes many Beryl problem, maybe somebody have to make it a "sticky" or something ?

Kuoi

---

