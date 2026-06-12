---
title: "[SOLVED] No Text in Many Fields, Need Help"
date: 2008-03-16
forum: Dell  Ubuntu Support
---

### Post by SteveRonan118 on 2008-03-16
I have tried searching for this, but have had no luck.
I just got Ubuntu last night and have been pretty happy with it.  I am running it on my second desktop HD with XP on the other HD.

However, I am having this problem where whenever I put my cursor over any system icons, where normally text would appear to provide more information, this does not happen.  All I get is a blank black box.  For example, I just dragged my cursor over the [I]System[I] tab at the top, and a very long black rectangle appeared.  Also, when I try to open the Terminal, all I see is a large blank white box.  There is not text in it, there is no text when I type, and no response to any commands, (not that I really know any).

Any help would be appreciated, and I am sorry to bother the forum so early in my Ubuntu quest...

---

### Post by Antarctica on 2008-03-16
Try reinstalling Ubuntu from the Live CD, but first, at the Live CD menu, go to the option that says "Check disk for defects."  It's possible that you could've burned the disk with errors.  If that's the case, then burn the disk again at the lowest speed setting.

---

### Post by SteveRonan118 on 2008-03-16
I checked the disk for errors when I ran the live CD.  It was fine.  I also checked against the Hash thing (forgot what it was called) and that was the same.

The script wasn't doing this about 3 hours ago.  I am trying to think of anything I did to make it stop working.  I can think that perhaps when I installed Firestarter, something happened?

---

### Post by Antarctica on 2008-03-16
I've never encountered this error before.  It could be a number of things... a GDM theme problem, a graphics driver problem, and I doubt Firestarter caused the problem.  What are its dependencies?  You can see if it's a theme problem by creating a new user for the purpose of testing.
```
sudo useradd -d /home/testuser -m testuser
sudo passwd testuser
```
When you're done, just type...
```
sudo userdel testuser
sudo rm -r /home/testuser/
```

---

### Post by SteveRonan118 on 2008-03-16
I can't seem to get anything to work in the Terminal.  All I get is a blank white box.  I can't see what commands I am typing or anything.  When I hit enter, nothing happens.  You can see the white Terminal window in the second photo.

Here are a couple shots of my problem.  You can see the black rectangles at the bottom where NoScript is running, as well as under my cursor where I am pointing on an item that would normally give me an information box or something.

Sorry about all the large photos and stuff.
Thank you again for all the help.

[IMG]http://i254.photobucket.com/albums/hh104/SteveRonan118/Screenshot.png[/IMG]

[IMG]http://i254.photobucket.com/albums/hh104/SteveRonan118/Screenshot-2.png[/IMG]

---

### Post by Antarctica on 2008-03-17
> **SteveRonan118 said:**
> I can't seem to get anything to work in the Terminal.  All I get is a blank white box.  I can't see what commands I am typing or anything.  When I hit enter, nothing happens.

Here are a couple shots of my problem.  You can see the black rectangles at the bottom where NoScript is running, as well as under my cursor where I am pointing on an item that would normally give me an information box or something.

[https://netfiles.msu.edu/?path=/afs/msu/user/r/o/ronanste/web/Screenshot-1.png](https://netfiles.msu.edu/?path=/afs/msu/user/r/o/ronanste/web/Screenshot-1.png)

[https://netfiles.msu.edu/?path=/afs/msu/user/r/o/ronanste/web/Screenshot.png](https://netfiles.msu.edu/?path=/afs/msu/user/r/o/ronanste/web/Screenshot.png)
Try again.  All I'm getting is an MSU login screen.

---

### Post by Antarctica on 2008-03-17
Weird.  Have you tried turning off Compiz?

---

### Post by SteveRonan118 on 2008-03-17
OK, thanks to Antarctica, problem is solved.
I had a bad theme apparently.  Switching back to Human solved it.
Many thanks.

---

