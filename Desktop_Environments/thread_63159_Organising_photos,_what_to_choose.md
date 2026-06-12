---
title: "Organising photos, what to choose ?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by djib on 2005-09-07
Hello,
Since I bought my camera I took about 5000 photos. I have sorted them all in different folders, but I gotta say, it starts to be a big mess despite all my efforts.
What is the best solution (and software) to organise all my photos?

[list]
[*]Are there Tags for photos, just like mp3s? In that case I could just tag all my photos.
[*]I know that digikam has some keyword feature. I would find it convenient if I could input keywords like for instance : 'animal', 'cat' and 'bestphotos' to one photo in order to be able later to show all photos of animals I have taken that I really like. But is it something used just by digikam or is it compatible with any other software? Because if I some day decide to stop using digikam, I don't want to rewrite all my tags again.
[*]Have you ever used ImgSeek, digikam, or any other program? Which one is the best according to you?
[/list] 

If you have any idea, advice, ...

Thank you very much!

---

### Post by MetalMusicAddict on 2005-09-07
F-Spot. ;) Its great.

---

### Post by McAviti on 2005-09-07
If you like dynamic web applications i'd recommend pixory. it is either a standalone app or can be integrated into a app server.

---

### Post by djib on 2005-09-07
[QUOTE=MetalMusicAddict]F-Spot. ;) Its great.[/QUOTE]
 F-spot looks a lot like digikam doesn't it ?
Do you know it the keyworkd that you input in F-Spot can be read by digikam et vice versa?

---

### Post by djib on 2005-09-07
[QUOTE=McAviti]If you like dynamic web applications i'd recommend pixory. it is either a standalone app or can be integrated into a app server.[/QUOTE]
 Hello,
pixory looks great!
I just wonder a few things that are not in the features list :
[list]
[*]Can you create those tags I'm looking for to be able to create some kind of dynamic albums.
[*]My photos are on an external disk. What will happen when my disk is not on...
[/list]

Thanks.

---

### Post by ralphdewitt on 2005-09-07
[QUOTE=djib]Hello,
Since I bought my camera I took about 5000 photos. I have sorted them all in different folders, but I gotta say, it starts to be a big mess despite all my efforts.
What is the best solution (and software) to organise all my photos?

[list]
[*]Are there Tags for photos, just like mp3s? In that case I could just tag all my photos.
[*]I know that digikam has some keyword feature. I would find it convenient if I could input keywords like for instance : 'animal', 'cat' and 'bestphotos' to one photo in order to be able later to show all photos of animals I have taken that I really like. But is it something used just by digikam or is it compatible with any other software? Because if I some day decide to stop using digikam, I don't want to rewrite all my tags again.
[*]Have you ever used ImgSeek, digikam, or any other program? Which one is the best according to you?
[/list] 

If you have any idea, advice, ...

Thank you very much![/QUOTE]

The tags and comments used by digikam are stored in SQLite database the is unique to digikam. I believe that you will find that all tag's and comments used in a photo ablum will be unique to that program.

I hope this helps some what.

---

### Post by McAviti on 2005-09-07
[QUOTE=djib]Hello,
pixory looks great!
I just wonder a few things that are not in the features list :
[list]
[*]Can you create those tags I'm looking for to be able to create some kind of dynamic albums.[/list][/QUOTE]
I'm not aware that this is possible, but it really sounds like a good feature. :) 
maybe i could help implementing something like that, since i'm a java developer myself. on the other hand that seems not as a simple task to me, since the data model of pixory is complex. but i'm sure therefore it would be principally possible to implement it.
[QUOTE=djib]
[list]
[*]My photos are on an external disk. What will happen when my disk is not on...
[/list]
[/QUOTE]
well, of course this would do no good to the application. pixory stores it's thumbnails in subfolders called '.album'. additionally a lot of metadata is stored there as well. i think it would be possible to store this structure on another place, but that's another feature request as well.

---

