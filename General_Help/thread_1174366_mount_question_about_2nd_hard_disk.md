---
title: "mount question about 2nd hard disk"
date: 2009-05-30
forum: General Help
---

### Post by lucifuge on 2009-05-30
I'm having to do a fresh install of Jaunty due to some issues.

I physically have a C and D drive and managed last time to successfully mount both drives. However, the D drive was mounted into what appears to be  /mydata.  IS it possible at install to have it a folder WITHIN the HOME folder...ie so its nested?

What i want to see is the D drive mounted to look like    /Home/Brett/mydata....NOT   at off the root  '/'.  The problem I think maybe is that while it knows HOME  it  may not know me, ie Brett   at partition time?  Or will it work fine?

I jsut want all of my 2nd drive as a nesting within HOME that's all. it's easier to navigate and have it looking like a larger sinlge directory strutures than one that splinterred off into two.

---

### Post by geraldvillorente on 2009-05-30
Use symlink...

---

### Post by lucifuge on 2009-05-31
if that's meant to help, it doesn't.   wtf is simlink

---

### Post by dandnsmith on 2009-05-31
What he's saying is use
*link -s xxx yyy*
to put a symbolic link (see the man page for link) to /mydata in /HOME/Brett.
Then, when you change directory to /HOME/Brett/mydata, you will end up in /mydata.
If that is good enough for you, OK,
 otherwise you'll need to change the mount point for /sda2 to be /HOME/Brett/mydata, having first created /HOME/Brett/mydata as a directory.You'll need to change the entry in fstab to make this permanent - but you can do it via the GUI (but I've forgotten exactly where that bit is - probably System|Admin)

---

### Post by lucifuge on 2009-05-31
no no,  I'm doing a fresh install from the jaunty CD install

I'm at the advanced partition screen.   It recognizes two HD's   120Gb each. I would prefer the following, but dont know if its possible:

- 2Gb swap
- 20Gb for system (root)
- and remainder (240-2-20) = 218Gb for data.  BUT 218Gb is across TO HD's,  how to set mount points??

---

### Post by dandnsmith on 2009-05-31
OK - if you're at the partitioning stage of an install, then you won't be able to do it all at once - you have to get the basics right (allocate for / and swap, and possibly another), do the install, and then fix the mount point so that the rest of the space from the 2 HDDs appears at the place in the hierarchy.
You won't, if sensible, try to span a filesystem (or part of it) across 2 HDDs, so get to the point where you can login, and have home space, and then sort it out.

Sorry, I cannot see how to clarify it further, as I don't know enough about your mental model of the space on the system (got blinded by doing it too long, I guess)

---

### Post by lucifuge on 2009-05-31
OK, I'm back where i originally was with a /HOME/BRETT and a /MYDATA. I will look into the methods. is the 'link' idea a mapping sort of approach?  Does it remember it from new startup each day?

---

### Post by dandnsmith on 2009-06-01
Yes it is a sort-of-mapping, but has limitations.
It will persist, once set up, until you delete the link.

---

