---
title: "Text comparison software???"
date: 2009-05-20
forum: General Help
---

### Post by clementeb on 2009-05-20
Hello,

I am writing to ask for some suggestions.
I have a series of documents in utf8 and East Asian encodings that I would like to compare among themselves, that is to see what parts of which are contained in the others. What is the best software or category of software to do such a task?
All I could think of are the copycat control software used in the universities to make sure that students don't simply copy and paste, but I don't know if there are linux versions of them. And perhaps there are simpler and faster options.
Cheers

---

### Post by dandnsmith on 2009-05-20
A tricky job that, but you might find *diff* and *diff3* do some of the job.
There may be gui tools, but I haven't had the need for such for a long time.

---

### Post by colau on 2009-05-20
[File comparison]("http://www.handlewithlinux.com/Linux-GUI-diff-utilities-a-visual-tour")
This may help.

---

### Post by cb951303 on 2009-05-20
[http://meld.sourceforge.net/](http://meld.sourceforge.net/)

this should work

---

### Post by kpkeerthi on 2009-05-20
[http://www.getdeb.net/app/Meld]("http://www.getdeb.net/app/Meld")

---

### Post by clementeb on 2009-05-20
Thank you very much for the ultra fast replies.
Diff and meld seem quite interesting, but they are not exactly what I am looking for since I have many hundreds of files to compare.
My idea is more or less this one:
1. select the texts (let's say a 100)
2. run the program
3. have as a result information for each text, like this in text A there is this and this line or string equal to text B, this and this line or string equal to text C etc. Of course, there would be the doubles (if text A has some of text B, then the opposite is also true)
Is there anything that can do such a thing? Also commercially or for other platforms?
Cheers

---

