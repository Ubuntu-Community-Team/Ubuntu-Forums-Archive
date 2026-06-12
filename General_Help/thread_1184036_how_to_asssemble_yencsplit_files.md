---
title: "how to asssemble yenc/split files"
date: 2009-06-10
forum: General Help
---

### Post by jeremyjjbrown on 2009-06-10
I've done a lot of work with .rar and .par2 files but lately I am seeing a lot of what I think are yenc and split archives around. Can anyone tell me how to reassemble into the original.

Thanks.

---

### Post by blueridgedog on 2009-06-10
Most newsreaders automatically assemble and decode yenc encoded files for you.  Doing it by hand would be a challenge.  I use Pan on Ubuntu and it handles them well.

---

### Post by jeremyjjbrown on 2009-06-11
Thanks,

Pan downloaded the yEnc files from the nzb I made at binsearch but did not assemble them. 

Any pointers?

---

### Post by michy99 on 2009-06-11
How are the files named? If they are like somefile.something.001, somefile.something.002, somefile.something.003, etc, then they are parts of a split file. If so I can show you how to put them together again with the cat command.

---

### Post by jeremyjjbrown on 2009-06-11
Yes. they are formated in a way like you describe.

filename.avi.001 filename.avi.002 and so on.

Thanks for your help.

---

### Post by michy99 on 2009-06-11
Open a terminal and change to the directory where the files are located. Enter:```
cat filename.avi.* > filename.avi
```Of course you replace the word 'filename' with the actual name of the file. This will create a new file which is just the separate files put together.

---

### Post by jeremyjjbrown on 2009-06-11
Thanks

---

### Post by michy99 on 2009-06-11
That is what the wildcard (*) is for. It will join all the files in numerical order. As long as they are named correctly, they will be joined in the right order.

You only need to run it once, no matter how many files there are. If the files you want to join are the only files in the directory, then it is even simpler.```
cat * > NameForJoinedFile
```Both versions depend on the files being named so that they will be added in the correct order.

---

