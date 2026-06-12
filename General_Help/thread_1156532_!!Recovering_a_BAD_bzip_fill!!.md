---
title: "!!Recovering a BAD bzip fill!!"
date: 2009-05-11
forum: General Help
---

### Post by dhysk on 2009-05-11
Well, I decided to finally switch to a 64bit solution, and at the same time I decided Jaunty had enough improvements that I would also go with it.  Anyway among a hundred other headaches, not all Jaunty related, one of my .bz2 files, of course the most important one with over 8 GB, somehow became corrupt.  


If you get an error when trying to decompress your .bz2 file it and it says something like:

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

If you get this this is what I did after searching mulitple tutorials this is the 'easiest' way for me.

[B]This is how I fixed it if anyone else runs into this issue.
[/B]

**1.**  Run the bzip recovery tool.  This will give you a ton of smaller rec*.bz2 files.
```
bzip2recover badfile.bz2
```

**2.** If your feeling lucky then
```
bzip2 -dc rec*.bz2 > praythisworks
```

**2a.** then simply untar the new file
```
tar -xvf praythisworks
```

I was not so lucky I couldn't even get step 2 to work.  A lot of the  time step 2 will fail or when you untar the new file (step 2a) it will stop when it gets to the corrupted blocks.  After claiming to search for the next header it will quit.  So now we have to find the corrupted blocks.

**3.**  Find the corrupted blocks
```
for i in *.bz2; do bzip2 -tvf $i >> corruptblocks.out 2>&1; done
```

**3a.** Search the test results for errors.  I open up the corruptblocks.out file in gedit and did a search for CRC.  Once found, delete or move the rec<yourcorruptedfile>.tar.bz2 file.
```
mv rec<yourcorruptedfile>.tar.bz2 /broken/
```

**4.**  Recombine the remaining files
```
bzip2 -dc rec*.bz2 > newdatafile
```

**5.**  Untar the new file.  Pay attention to the last output in the terminal for example: /home/<username>/Documents/tosted.doc
```
tar -xvf newdatafile
```

**6.**  Now we have all our data back up to the corrupted block.  I found a nice little perl script from another tutorial that finds the header files in a tar.  Run the perl script against your file and have it output to a log.
***link to header perls script:*** [http://oss.bestsolution.at/documents/find_tar_headers.pl.bz2](http://oss.bestsolution.at/documents/find_tar_headers.pl.bz2)
```
perl find_tar_headers.pl newdatafile >> headers.log
```

**7.**  Open up the headers.log file and find the header number that follows your last file that was uncompressed in the output.log.
Example: newdatafile:920193537:home/<username>/Documents/tosted.doc:3446121254
         newdatafile:**1399059577**:home/<username>/Documents/another.doc:26115573

The bold number is the header number you need.

**8.**  Extract the last part of the newdatafile tar into a new tar
```
tail -c +13399059577 newdatafile > taildfile.tar
```

**9.**  Finally untar the new file
```
tar -xvf taildfile.tar
```

**10.**  If you get errors in this last step repeat steps 8 & 9 until you get to a header number that works.  I never had to but that probably would have been my next step.

Anyway I hope this helps, loosing data sucks, and I apologise for my bad communication skills if this was hard to read.

---

### Post by geraldvillorente on 2009-05-11
Great! Thank you dhysk....This is really helpful...

---

