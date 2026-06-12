---
title: "Files lost mid-transfer from Ubuntu to iRiver - System Volume Information?"
date: 2006-04-18
forum: Desktop Environments
---

### Post by matthewrevell on 2006-04-18
Howdy,

Last night, I moved a whole load of files from my Ubuntu desktop to my iRiver H340. The transfer seemed to go okay but the files haven't shown up on my iRiver (they have been removed from my Ubuntu machine, though).

I now have a System Volume Information directory on my iRiver with around 1 GB of files, none of which I can even open in gEdit. Are my files locked up in there?

The only odd thing I can remember is that, after I unmounted the iRiver, I couldn't re-mount the device as Ubuntu said it was already mounted - needless to say, I couldn't actually access it.

Any thoughts?

Cheers all :)

Matthew.

---

### Post by Miguel on 2006-04-18
I think you have just suffered a terrible bug in gnome-vfs. This probably won't help you, but this is why Dapper performs some checks everytime a volume is dismounted (even in read-only mode).

BTW: System Volume Information is a folder where windows stores some found files after a scandisk or something similar. At least, that's what I remember. I have lost some files there after copying files from ubuntu to a windows partition while windows is hibernated.

---

### Post by matthewrevell on 2006-04-18
Thanks for the reply.

Arg, that's a pain. I take it the files are lost forever and the System Volume Information directory is, in this case, of no relevance.

---

### Post by Miguel on 2006-04-18
Have you deleted the folder???

If not, you can try to recover something. It may be a bit painful, though. For this to work, try to copy the System Volume Information folder to your HD and delete it from the iRiver. Next thing you should try is identifying the file types. 

Unless Windows (and I've seen OS X not doing this) Linux (and BSDs) can understand file types without an extension. And audio files (at least oggs) are not plain text so opening with gedit wouldn't help.

Just fire a terminal, change to the System blablabla folder, and then type
```

$ file name-of-a-file

```

If it says something like Ogg Vorbis, you can try two things. First one is renamig it to name.ogg and playing with totem (or xmms or whatever). If you don't recognize the file type, you can always navigate to that folder using nautilus and double-click on a file to see what happens.

And, yes, this is a pain where the sun doesn't shine... but it might actually help you save some time (if you don't have the cd's at hand). 

Finally, yes, I have lost data due to this late-discovered bug. There was an osnews story out there. A friend of mine has also lost data to it. And the fix in dapper is a bit of a hack (I read the bug was quite intrincated). So the moral is: if it is important data, copy it, don't move it. And check twice you have it before deleting the redundant copy.

---

