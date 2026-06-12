---
title: "emacs and firefox-like tabs"
date: 2006-03-03
forum: Desktop Environments
---

### Post by ubuntumaneh on 2006-03-03
Does someone know if I can use tabs (in the sense of firefox, for instace) in emacs21?       
Something like the name of the buffer being shown in a respective tab, just like we see a    
web site per tab in firefox. It would be nice to change buffers with alt+tab. 
Does the new cvs-emacs have this feature?
In case of positive answer, which is a link or how to use this feature?

Im already looking at google. Just to want to increase my options.

Thanks

---

### Post by jpkotta on 2006-03-03
I think the speedbar has something like a list of buffers that acts like tabs.  Personally, I use C-x b and tab completion.  C-x b TAB will bring up a (clickable) list of buffers.

---

### Post by ubuntumaneh on 2006-03-03
Thanks for the reply.

Actually I used both method you suggested, speedbar and "C-x b". They are good. But I think what I would like is something more similar with firefox. I would like to see the name of all buffers in tab, just like firefox or gedit, instead of going to another windows. It seems this is possible in xemacs. But I would like to have  this in emacs21.

---

### Post by lukew on 2007-01-04
> **ubuntumaneh said:**
> Thanks for the reply.

Actually I used both method you suggested, speedbar and "C-x b". They are good. But I think what I would like is something more similar with firefox. I would like to see the name of all buffers in tab, just like firefox or gedit, instead of going to another windows. It seems this is possible in xemacs. But I would like to have  this in emacs21.

There is C-x b 

And there is C-x C-b

The latter gives you as list of files within a buffer which you can select to open ( C-x o to cycle onto the buffer and then return once you are upon the file ) ( or click with mouse)

C-b a[TAB] auto complets. 

Also (icomplete-mode 1) shows files matching what you typed while you are typing!

I hope this helps.

Luke

---

### Post by ScubaDo on 2007-01-06
> **ubuntumaneh said:**
> Does someone know if I can use tabs (in the sense of firefox, for instace) in emacs21?       
Something like the name of the buffer being shown in a respective tab, just like we see a    
web site per tab in firefox. It would be nice to change buffers with alt+tab. 
Does the new cvs-emacs have this feature?
In case of positive answer, which is a link or how to use this feature?

Im already looking at google. Just to want to increase my options.

Thanks
There is something similar to what you are looking for in package emacs-goodies-el. After the package is installed just say M-x tabbar-mode.

Luis

---

