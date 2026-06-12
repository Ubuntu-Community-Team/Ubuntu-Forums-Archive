---
title: "Middle Mouse Wheel Button Problem"
date: 2014-02-20
forum: Desktop Environments
---

### Post by wireaddict on 2014-02-20
Greetings: I'm a relative newbie here & I'm trying to implement a fix I found here for a mouse scroll wheel button problem: [http://ubuntuforums.org/showthread.php?t=2092090](http://ubuntuforums.org/showthread.php?t=2092090)  My question is how do I create the hidden file ".Xmodmap" shown in the second from the last post?  It doesn't appear that I can do it from the terminal.  Thanks & regards.

---

### Post by deadflowr on 2014-02-20
Open up the text editor Gedit, follow the instruction of adding that pointer line. 
And when you save the file, simply type it as .Xmodmap.
Make sure it is saved in the home folder and not in another one, like Downloads or Documents.

You can verify that it is in the right place by opening up the Files(home folder) and pressing ctrl + h to view hidden files/folders.
If done right the file will be in the same screen as the normal folder layout(ie Downloads, Documents,Pictures) as well as several other hidden files and folders.

Hope this helps.
Or makes sense.

(Added bonus info, the ~ symbol means the home folder, in shortened form
So ~/.Xmodmap means /home/username/.Xmodmap)

---

### Post by wireaddict on 2014-02-21
Thanks deadflowr.  In other words, I needed to open Gedit in the Home file & add the the content from the link I posted.  That's what I did although some of it was guesswork but, happy to say, it worked so this matter's resolved!

---

### Post by wireaddict on 2014-02-21
To make it official I added the word "Resolved" to the title.

---

### Post by deadflowr on 2014-02-21
> **wireaddict said:**
> To make it official I added the word "Resolved" to the title.

You can mark the thread as solved by going up to the top of the page area where it says Thread Tools.
(It should be at right above the first post on the right side)

---

