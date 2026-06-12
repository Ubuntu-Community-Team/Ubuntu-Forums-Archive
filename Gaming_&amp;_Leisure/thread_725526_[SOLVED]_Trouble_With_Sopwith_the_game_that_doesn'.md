---
title: "[SOLVED] Trouble With Sopwith the game that doesn't want to close"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by Halcyon31415 on 2008-03-15
I just installed Sopwith and it doesn't want to close when I click on the close button. I'm still very new to Unbutu, so I hope i'm not wasting anyones time with trivial questions, but does anyone else have this problem/solution? 

I downloaded the game through
Applications:
Add/Remove:
Sopwith

In case that matters. 

For what ever it's worth I love Unbutu and really want to learn more about it and linux in general. 

Well thx for your time.

---

### Post by Halcyon31415 on 2008-07-26
My friend showed up and got me to understand how to use the terminal. Sorry this is really basic but here is how you kill sopwith. 

type:
ps -e (this will bring up all the processes running on the computer, look for Sopwith there will be a pid number next to it)
kill -9 (pid#)

This should get rid of the game sopwith. Now you/I can enjoy playing the game with out re-starting the Computer.

---

### Post by FranMichaels on 2008-07-26
Having played sopwith since I was 3 (the version you are using is a port, luckily the author released the source!)
to close it, both then and now:

Press *ctrl + c*

Also, in general for software, 
```
pkill nameofapp
```
or 
```
killall nameofapp
```

Will close it too. :D

Also, take a look at the man page for sopwith
```
man sopwith
```
There are probably a few keys you haven't discovered (like pressing h to head to home base.)

---

### Post by Halcyon31415 on 2008-07-30
Thank you for you help. I played sopwith when i was a boy. I could only get to the end on my really slow XT computer. We had an 286 as well but that was just too fast for me ;) I do remember the home key but I can't recall the cow's or the birds or missiles. Where they in the original game? I think i would like to close this topic and say it was answered, but i don't know how to do that.

---

