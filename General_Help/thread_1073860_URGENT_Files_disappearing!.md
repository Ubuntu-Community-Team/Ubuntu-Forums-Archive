---
title: "URGENT: Files disappearing!"
date: 2009-02-18
forum: General Help
---

### Post by Envergure on 2009-02-18
Most of my three semesters' physics work is gone!  Is there a file retrieval util that may be able to save them?  If not it may cost me the course.

I have not had any problems with Windows, so I don't think it's my hard drive.  My only theory so far is that AVG has been removing "threats" from my Linux partition.  I have removed the IFS for ext3 but that doesn't seem to have stopped it.

Also, nothing seems to be missing from any other folders.  Just those ODT docs.

For the future, is there something for Linux like Apple's Time Machine?

---

### Post by Nexusx6 on 2009-02-18
Oh no! Lets hope that the forums can help you figure out what the heck is happening. 

It would seem very odd for AVG to delete .odt with no justification. Almost every anti-virus program for years now quarantine files before deleting them for the exact reason that you have. Though I doubt it is your anti-virii, have you tried checking its quarantine section/folder?

Also, try running this in terminal to find all odt files on your system:
```
sudo find / -name *.odt -print | less
```
It should give you a list of all odt files on your partition (and any mounted media) line by line. If they've been accidentally misplaced or saved in the wrong area, they'll show up this way. To narrow the search down, you could of course replace the asterisks with the name of a file you remember, but try leaving it in there on a first run. 

Best of luck!

---

### Post by Envergure on 2009-02-21
Didn't find them.  I have determined that AVG is not the problem (99% sure).
If anyone knows any good data recovery or backup programs pls let me know!

---

### Post by akudewan on 2009-02-21
Try Photorec: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I've used it once:
[http://bit-rot.blogspot.com/2007/04/photorec.html](http://bit-rot.blogspot.com/2007/04/photorec.html)

---

### Post by drs305 on 2009-02-21
Is it possible that the files could have been saved in MSO format at some point? Does AVG have a quarantine folder?

Here is the link to the ubuntu official documentation on data recovery, but I don't believe it would apply in this case, which appears to be specific file(s) deletion. 

[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

If they were in NTFS format there is an app called ntfsundelete - part of the ntfsprogs package.

---

