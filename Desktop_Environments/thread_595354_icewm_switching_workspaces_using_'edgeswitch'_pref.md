---
title: "icewm switching workspaces using 'edgeswitch' preference"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Kirky_D on 2007-10-28
Hi there!

Just started using icewm. Been messing about with the settings and whatnot. I really like switching between workspaces by moving my mouse to the edge of the screen, icewm provides this feature by setting:
```
 EdgeSwitch=1 
``` 
in the preferences file. I've done this and restarted icewm but it doesn't seem to have worked. Any body know what the problem might be?

Cheers!!

---

### Post by aysiu on 2007-10-28
Make sure it says: ```
#  Workspace switches by moving mouse to left/right screen edge
EdgeSwitch=1 # 0/1
``` and not ```
#  Workspace switches by moving mouse to left/right screen edge
# EdgeSwitch=1 # 0/1
```

---

### Post by Kirky_D on 2007-10-28
Yea, i've uncommented it. 

Thanks though

---

### Post by aysiu on 2007-10-28
Works for me in Gutsy right now.

When you say it doesn't seem to work... what exactly happens when you hold your mouse to the edge of the screen?

By the way, when I just tested it, I had to hold the mouse for about a quarter of a second before it actually switched to the next workspace.

Is it possible you don't have four workspaces available to switch to?

---

### Post by Kirky_D on 2007-10-28
I do have four workspaces. When i put my mouse to the edge of the screen, nothing happens whatsoever. I leave it there for quite a few seconds and still nothing. I can switch between workspaces by clicking on them at the bottom and by ctrl+alt+[left/right]. 

I'm pretty stumped on this one to be honest

---

### Post by aysiu on 2007-10-28
Can you create a new test user and see if you can make the edge switch work for that user?

---

### Post by Kirky_D on 2007-10-29
Yes, creating a new user and changing the edgeswitch does actually work. So I must have changed a setting somewhere else that i dont know about.

any hints?

---

### Post by aysiu on 2007-10-29
Not sure what to do next, but it means there's something wrong with your current user's profile.

Is it possible you have EdgeSwitch in your preferences file twice (once with 1 and once with 0)?

I don't know what else to look for.

---

### Post by Kirky_D on 2007-10-29
Ok, well thanks for the help. I have had a look through my entire preferences file and found nothing out of the ordinary. 

But i have got it working. Basically i renamed my preferences file to .preferences and placed the settings i wanted in a new file called preferences and it seemed to do the trick. I am gonig to keep the old preferences file there as a reference and just use my own file from now on.

No idea what the problem was

cheers

---

