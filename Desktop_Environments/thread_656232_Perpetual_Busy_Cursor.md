---
title: "Perpetual Busy Cursor"
date: 2008-01-02
forum: Desktop Environments
---

### Post by lohcs on 2008-01-02
Hi guys, Just wondering if I had done something wrong.

I just rebooted my machine and now when Gnome loads, it shows a spinning busy cursor. I didn't change any cursor sets though.

I tried looking at the processes and don't see its waiting for anything. The system is still responsive though. 

So was wondering if you guys know why the cursor is perpetually busy and spinning ?

Thanks.

---

### Post by lohcs on 2008-01-02
Anyone have any idea ?

---

### Post by kmyram on 2008-02-23
I have the exact same problem, and it's driving me crazy - nothing in the logs indicate a problem, no processes run amok, no nothing to shine a little light on the issue... just a stupid spinning cursor!

Anyone?

---

### Post by NiceGuy on 2008-02-27
I know it doesn't help, but your not alone! :confused:

I too have done and extensive search of the processes running and... well there isn't anything!

When I disable 'show_desktop' under 'nautilus > preferences' in the gconf-editor this seems to stop it happening (but I obviously lose all my icons etc.) and re-enabling it causes it to come back :(

Interestingly, I created a new user and this users desktop does not suffer a similar affliction, and although I don't relish the thought of deleting the contents of my home folder its looking like that might be the solution as this thing is getting rather annoying now!

I'll continue 'tinkering' and report back if I have any success.

---

### Post by NiceGuy on 2008-02-27
GOT IT!

As with all these things, the solution was annoyingly simple.

In my .gtk-bookmarks file (in the home folder) I had a folder listed which was on a remote machine and was no longer available. Removing this entry solved the problem.

eg. Contents of my .gtk-bookmarks file 

```
file:///home/user/Music
file:///home/user/Pictures
file:///home/user/Videos
x-nautilus-desktop:///Music%20on%20server.volume       <- removing this line and re-logging solved the problem
```

Hope this helps others.

---

### Post by ichigo600 on 2008-05-04
thank you very much for figuring this out. the same thing bugged me since about 1 month. i even registered here just to let you know i appreciate it.

---

### Post by djinn23 on 2008-05-05
Fixed me!! Thanks!

---

### Post by elisha on 2008-06-06
Hello Mr Nice guy,
I have the perpetual busy cursor as well.  Thanks for your post, but could you give some more detail for a beginner?  I opened my home folder and did not see a .gtk.
If I open the terminal, what should I type to find this problem?
Thanks

---

### Post by NiceGuy on 2008-06-07
Hi elisha,

The clue is in the file name. The file your are looking for is:

**.**gtk-bookmarks

The fact that it begins with a '.' means that it is a hidden file.

In order to reveal it you will need to open up your home folder, go to View and then click 'Show hidden files'. Alternatively you can use the shortcut key which is Ctrl+H

Hope that helps!

---

### Post by elisha on 2008-06-10
Thanks Nice,
My .gtk file said this when opened:
xnautilus/// "CD-RW%2FDVD%C2%B1RW%20Drive%20(2).volume
  
I deleted this line, though it wasn't identical to yours.
Hope this works!
Thanks
Elisha

---

### Post by elisha on 2008-06-10
Yes, It worked! 
How did you ever figure that out??
Good job
E

---

### Post by NiceGuy on 2008-06-14
Hehe, it was a case of good ol' trial and error :P I backed up my home directory and... well... deleted files which affected nautilus one by one till removing one fixed the problem :P

On closer inspection of that file it became obvious what the problem was.

---

