---
title: "Americas Army Hell!"
date: 2005-05-05
forum: Gaming &amp; Leisure
---

### Post by DutchLau on 2005-05-05
Okay, I've been playing Americas Army for a while now on Linux and windoze alike. Now I only use Linux. I've installed it successfully on 3 linux computers without any problems, I got my new computer 2 days ago (see sig) and I downloaded Americas Army. The only thing is, it won't install! 

The filename is armyops230-linux.run (Filesize 744.9 Mb - Which is normal, I think) and I've done various things to try get the file working. I'm downloading a new file because I think it's corrupt, but how can that be? I used D4X.

I did >  chmod +x armyops230-linux.run  to get it executable and then >  sudo sh armyops230-linux.run  and >  sudo ./armyops230-linux.run  give me the same error message:

>  discom@Discom:~$ sudo sh armyops230-linux.run
armyops230-linux.run: line 1: !doctype: No such file or directory
armyops230-linux.run: line 2: html: No such file or directory
armyops230-linux.run: line 3: head: No such file or directory
armyops230-linux.run: line 4: title: No such file or directory
armyops230-linux.run: line 5: meta: No such file or directory
armyops230-linux.run: line 6: !--: No such file or directory
armyops230-linux.run: line 7: link: No such file or directory
armyops230-linux.run: line 8: meta: No such file or directory
armyops230-linux.run: line 9: meta: No such file or directory
: command not foundn: line 10:
armyops230-linux.run: line 11: /head: No such file or directory
: command not foundn: line 12:
armyops230-linux.run: line 13: body: No such file or directory
armyops230-linux.run: line 14: !--: No such file or directory
armyops230-linux.run: line 15: table: No such file or directory
armyops230-linux.run: line 16: tr: No such file or directory
armyops230-linux.run: line 17: syntax error near unexpected token `<'
armyops230-linux.run: line 17: `                        <td width=7 rowspan=3><img src="http://www.3dgamers.com/i/imgs/space.gif" width="7" height="1" border="0' alt=""></td>


What's going on? 

Please could someone help me out with this? It's damned annoying,

Thanks already,

DutchLau

---

### Post by shakin on 2005-05-05
I'd go with the corrupt file theory. It installed fine for me.

---

### Post by DutchLau on 2005-05-05
What was the AA filesize for you?

---

### Post by tread on 2005-05-05
My install worked fine, heres the md5sum for the file I downloaded. Compare it with the file you have to see if its a corrupt file problem.

md5sum armyops230-linux-1.run
a0df99cc9933120905f2de51f2ad613b

---

### Post by DutchLau on 2005-05-05
Hello,

Thanks for the reply. I'm guessing this is the wrong checksum:

> fb0647d0f859107de1d59a1d5bd02a0b  armyops230-linux.run 

Cheers,

DutchLau

---

### Post by DutchLau on 2005-05-05
FIXED!

The file was corrupted as I suspected,

Thank you Ubuntu community,

Cheers,

DutchLau

---

### Post by DutchLau on 2005-05-05
For those of you that don't believe in the power of Linux, I'm getting 240 FPS on SF Hospital (For those of you that don't know it its the most graphic intensive map in the game) and for GLX gears I have the following:

> 13878 frames in 5.0 seconds = 2775.600 FPS
13674 frames in 5.0 seconds = 2734.800 FPS
13899 frames in 5.0 seconds = 2779.800 FPS 

AMAZING.. 

I'm dumbfounded.  :) 

Cheers,

DutchLau

---

### Post by jdodson on 2005-05-06
[QUOTE=DutchLau]For those of you that don't believe in the power of Linux, I'm getting 240 FPS on SF Hospital (For those of you that don't know it its the most graphic intensive map in the game) and for GLX gears I have the following:

 

AMAZING.. 

I'm dumbfounded.  :) 

Cheers,

DutchLau[/QUOTE]

i get similar rocking framerates....... then again my new box has never had windows on it so im not sure if it would do better.... oh well, the games still look and play amazing:)

---

