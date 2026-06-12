---
title: "How to make a file disappear"
date: 2005-04-07
forum: Desktop Environments
---

### Post by sean_worker on 2005-04-07
Both my wife and my sister have run into this problem:

1. Open a document from the web (say from a web-based email site).
2. Edit the document, save changes.
3. Shut down the computer.
4. Turn the computer back on ...
... your file is gone!

I think this is what happens at least, and I think it is because when you open a file directly from the web it is put the the /tmp directory, and the /tmp directory gets cleaned every time the computer reboots (or shuts down, I'm not sure).

I guess you could disable /tmp cleaning, but then someone will have to go clean it up eventually or you will run out of hard drive space.

I am sure they are not the only people who have got caught by this.  And it is not just editted files either (I think my sister lost her desktop background by this same way).

I think this use case needs to be considered.  Users either need to be warned about this and given the opportunity to save their files elsewhere, or files opened from the Internet should be saved in another directory (say ~/.webfiles).

I don't think I can stress enough how important it is that this be addressed.  It makes the system seem unstable and unreliable.

---

### Post by carlc on 2005-04-08
What web browser are you using? I would think the problems that you are having are specific to your browser. I use firefox and have it set to save downloads in a directory called "downloads".

---

### Post by kiddo on 2005-04-08
Hmm, the only thing that comes to my mind is using SAVE AS, then you can't run into temp files problems :) and it keeps you better organized -- why would you want to keep your docs in a temp dir? How are you supposed to find them easily thereafter? Correct me if I misunderstood

---

### Post by sean_worker on 2005-07-11
OK, I ended up filling a bug.

It is number 8862 (see [http://bugzilla.ubuntu.com/show_bug.cgi?id=8862](http://bugzilla.ubuntu.com/show_bug.cgi?id=8862)).

---

