---
title: "permission help chmod etc..."
date: 2009-03-10
forum: General Help
---

### Post by thecha on 2009-03-10
I have a Samba server at our school.  It works great however I have one problem caused mainly by the Grade 1 students and I'm looking for a permissions solution to my problem... which I will try my best to explain...

We have a network share called Student.  Where students and teachers of the school can save their work to collaborate etc..

My chmod solution...  Here is what I've done to try to fix the problem...

chmod 555 student
chmod 777 -R 1A
chmod 777 -R 1B
chmod 777 -R 2A
etc...

Now when a student grabs folder 1A and drops it on 1B it creates a a folder Student/1B/1A/* then gives an error that 1A cannot me modifed... The folder Student/1A is left empty the contents is all in Student/1B/1A/

I was wondering if anyone had any other ideas about what I can do to stop this from happening...[-o<

I've attached a crude drawing to try to help explain the problem... 

[http://i43.tinypic.com/a9n0ip.png]("http://i43.tinypic.com/a9n0ip.png")

---

### Post by kngunn on 2009-03-10
I can't answer your question outright, but I think I can add a little guidance.

Your picture has the folders showing, but doesn't indicate shares.  Remember that shares and folders are two very different things with very different rights.  Are the folders you are indicating all in a single share or are they separate?

To avoid some of the messiness, I prefer to use the "force user" and/or "force group" options in my share definitions (/etc/samba/smb.conf).  That can prevent a lot of rights confusion.

---

