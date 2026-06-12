---
title: "Recover files?"
date: 2009-04-12
forum: General Help
---

### Post by josemaster2228 on 2009-04-12
hello people i hope that you could really help me with this this is very urgent today i installed ubuntu on a friends laptop and i backed up everything to her 8gb sansa view it all went nice but when it came back to putting the files i put the player in the mass storage mode and the files weren't there so i tried it on my windows/ubuntu machine using windows in both modes one time the stuff showed up i wanted to rar it so i unplugged it and plugged it back in same mode and now the files were not there i did nothing to it. so now i am starting to realize that i may be screwed using the player and now i need to find a way to do a hdd recovery after formatting to ext2 and at least get some files back this is for a friend and i really need this solved i have test disk installed but i have no idea how to use it and the guides are useless it would be very appreciated if you knew how to use test disk or recover the files or even help me get the files off the view since 3.5 gigs are still being stored on there so the files should still be there but they wont show on either mode on either os thanks

---

### Post by statistic on 2009-04-12
I think you may be more screwed on trying to recover from the formatted partition than from the sansa. I suggest looking into a linux util called "dd_rescue", which is for recovering damaged files, and try that with the sansa.

As for the hard drive, if you can remember whether you did a quick format, or a normal one. If you did a normal format, it writes 0 to entire partition, that's why it takes longer. If you did that you'd have to be REALLY tricky to get it back.

---

### Post by josemaster2228 on 2009-04-12
thanks for the quick response i dont think that the files in the sansa are damaged i think they are there because they still take up space. the format was the linux install btw. so am if ****** or what?

---

### Post by statistic on 2009-04-12
That fact that they take up space is exactly what dd_rescue is good at. It will find the files that are there even if the file table doesn't know where they are. 

The format in the Linux install I believe gives you a choice, but I think that the normal format is the default option.

Sorry I can't be of more help, I just thought you should try dd_rescue on the sansa from what I read. I'm don't know much past that about file recovery.

p.s. Did you do something special to get the sansa recognized? My linux won't recognize my sansa at all, it just ignores it completely.

---

### Post by josemaster2228 on 2009-04-13
to get the sansa view to be recognized you have to put the device on hold and then go and press the left button for bout 5 secs then plug the thing back in and it should be seen as a mass storage device

---

### Post by bumanie on 2009-04-13
You could try photorec - it is part of testdisk > sudo apt-get install testdiskThen to start photorec, > sudo photorecGo [here ]("http://www.cgsecurity.org/wiki/PhotoRec")to read a tutorial. Photorec finds multiple file types and is filesystem independent. Good luck.

---

