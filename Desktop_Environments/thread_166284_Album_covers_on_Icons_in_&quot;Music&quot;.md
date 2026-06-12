---
title: "Album covers on Icons in &quot;Music&quot;"
date: 2006-04-26
forum: Desktop Environments
---

### Post by markr on 2006-04-26
In WinXP I can stick an album cover jpeg in the directory of the album and call it Folder.jpg (hidden so it does not appear in the view).  I know in nautilus I can physicall assign a graphic (e.g. an album cover jpeg), but I was wonder if there is anyway nautilus can do this 'automatically' similar to the method above in WinXP.

Note a major issue, but I'm gradually moving everything across to Ubuntu, and would like the easiest transition possible (call me lazy!!).

Mark.

---

### Post by hezral on 2006-04-26
EDIT: sorry didnt see that u already know about it. 


maybe you could use the album art as the icon for that folder? 

open the folder's properties and change the icon from there. i'm think you can change folder icons.

so i you can do that..you could make your own custom icon folders even an icon with a jewel case and a cd cover?

---

### Post by markr on 2006-04-26
I think you are right,  I'll move all my album art into a separte directory and customise the relevant folder icons.

From a useability point of view, it would have been nice for nautilus to pick up jpegs from the folder and apply them automatically.

Other areas where I've noticed that WinXP gives a better user experience is my digital photograph collection, the folder icons automatically show a 'review' of the pictures in the folder.

Nautilus does this for files (my avi files for example show a frame of the media, pdf documents show the first page of the document), I would not have though it too difficult to apply the same logic to folder icons.

I suppose I would much rather have a rock solid OS (which is why I'm moving to Ubuntu),  I guess the fancy user effects come later...

Mark.

---

### Post by hezral on 2006-04-26
im not sure you can do this in nautilus or not but maybe you could make a script that changes the folder icons to the album.jpg file that are in the folder itself? 

i dont know much about scripting tho..

---

### Post by NinjitsuStylee on 2006-07-30
> **hezral said:**
> i dont know much about scripting tho..


Apparently neither does anybody else when it comes to this issue :(:(:(:(:(:(

---

### Post by billynomates on 2008-06-23
Hey guys, I haven't tested this out, although I plan to later, but there's a python script [here]("http://my.opera.com/sjosul/blog/2007/10/28/album-art-as-folder-icon-in-gnome") that is supposed to help you do this.

---

### Post by billynomates on 2008-06-24
> **billynomates said:**
> Hey guys, I haven't tested this out, although I plan to later, but there's a python script [here]("http://my.opera.com/sjosul/blog/2007/10/28/album-art-as-folder-icon-in-gnome") that is supposed to help you do this.

It works pretty well. Be sure to add the -r option to recursively traverse your music directory. Change line 13

default="[Ff]older.jpg",
to
```
 default="[Ff][Oo][Ll][Dd][Ee][Rr].[Jj][Pp][Gg]",
```

to make sure it sees all your jpegs.

---

### Post by Fingers &amp; Thumbs on 2008-06-24
Ah! man, change your name to billyonemate now, and I dare say, there will be more, I can't wait to get this going, nice one.

---

### Post by billynomates on 2008-06-24
> **Fingers & Thumbs said:**
> Ah! man, change your name to billyonemate now, and I dare say, there will be more, I can't wait to get this going, nice one.

You're welcome, and your signature is hilarious!

---

