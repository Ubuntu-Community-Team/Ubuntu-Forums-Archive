---
title: "Finding errors in Aspel not in text editors"
date: 2006-01-30
forum: Desktop Environments
---

### Post by JoeS on 2006-01-30
I saved a web page as plain text and edited it in Vim. 

This is what it looks like on the web: 

> The meal is set before us—perhaps early  

It looks alright when I open the file in Vim, Gedit, or Open - Office,

but when I spell check it with Aspell (version 5.50.5-5) I get this:

> The meal is set before us\uffff~@~Tperhaps early

It also changed:>  wasn’t 
 to  
 wasn~@~Yt

Why is Aspell finding errors in the file?
Is there a default with this program?

---

