---
title: "No hand cursor on flash buttons"
date: 2009-06-15
forum: General Help
---

### Post by trpnblies7 on 2009-06-15
I think this has happened ever since I updated to Flash 10, but whenever I'm dealing with an SWF file on a website, my mouse no longer turns into a hand icon when I hover it over a button or link. This makes it difficult to figure out what parts of the SWF file are clickable. Any idea why this is happening? Is there a fix for it? It's a minor issue, but it's pretty annoying.

I'm using Jaunty, but this happened with Intrepid, too.

Thanks!

---

### Post by trpnblies7 on 2009-06-15
Anyone?

---

### Post by trpnblies7 on 2009-06-15
Maybe?

---

### Post by Sebelious on 2009-06-25
Came accross this thread when I was trying to find a solution to this problem; Seems to be actionscript 3.0.
 
You need to set the buttonMode of the object to true, so if you had a movie clip called ubuntu you'd use this code:
 
ubuntu.buttonMode = true;
 
Now when ever the curser hovers over ubuntu it'll be the little hand.
 
Hope that helps

---

### Post by trpnblies7 on 2009-06-25
Thanks, but I think you misunderstood my problem. I'm not the one creating the files. I'm talking about just interacting with any SWF file on any website. The hand icon appears on Windows, but not on Ubuntu.

---

