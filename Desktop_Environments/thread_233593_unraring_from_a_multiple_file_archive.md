---
title: "unraring from a multiple file archive"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Vlatko on 2006-08-10
i downloaded a torrent and it's rared in about 50 parts. how do i extract the content? i can open all kinds of archives, i downloaded the utils with automatix. in windows i selected all the archives and selected extract here, i tried that in linux but it seems to be lasting ages. how can this be done? thanks!

---

### Post by maniacmusician on 2006-08-10
i remember when i had windows i used 7-zip to handle those. ubuntu has 7zip too, maybe that will work? try p7zip --help, or man p7zip for info on how to use it. 

If not, there's always HJSplit. I specifically pointed to the java one because it is the easiest to use; no installation, no nothing. as long as you have java, you can just execute it. It both joins and splits files.
[http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)

---

### Post by Vlatko on 2006-08-10
well i think i got it. i just selected the first archive and clicked extract, waited a min and the complete file was there. maybe in linux it recognizes the type of archive and you can extract from any of the archives. i tried the output file and seems everything is ok.

---

### Post by maniacmusician on 2006-08-10
awesome, thats good. I tried to do it the other day and it didn't work for me, I had to use HJSplit.

---

