---
title: "Copying 120,000 files"
date: 2005-09-09
forum: Desktop Environments
---

### Post by dk_pa on 2005-09-09
I just did a backup and am trying to move files off of my laptop.  I was playing with the xargs command but am not quite sure how to make it work with the cp command.

At first I was just going to break it all up into smaller directories but realized that would take forever.  This is also something that I'm sure will be useful to know for the future, of course.  I was browsing the web and saw a mix of results.  I've found many answers searcing here on the forums (like using the ndiswrapper -- nice write up btw), so thought I'd ask here first.

---

### Post by Juergen on 2005-09-09
I'm not quite sure what your problem is - ndiswrapper would only be useful if your network doesn't work at all, I think.

If your problem is only the time to copy so many files, I'd try to stuff them into a *.tgz and copy this.
A big single file often transfers much faster than loads of smaller ones.

---

### Post by John Nilsson on 2005-09-09
```
cd <dir/to/copy> && tar cf - . | (cd <dir/to/copy/to> && tar xvf -)
```

the short version beeing:

```
tar cC <dir/to/copy> . | tar xvC <dir/to/copy/to>
```

but the first version exposes much more bash magic to the learning linuxer  ;-) 

to do the same over a network

```

#On receiving end
nc -l -p 1024 | bunzip2 | (cd <dir/to/copy/to> && tar xvf -)
#On sending end
cd <dir/to/copy> && tar cf - . | bzip2 | nc -q 0 <receiving host> 1024

```

---

### Post by dk_pa on 2005-09-13
Hey guys, thanks for the help.  The mention of the ndiswrapper was just me thanking whoever wrote that up cause I was able to get my wireless working on my laptop.

I tried the commands (haven't had time to actually disect them yet) and they seem to work except I keep getting "destination full errors" when copying.

I have tried to copy the files to a portable hard drive with a Fat32 partition of 16 gb free.  The amount of files are only 7 gb.  It seems like it's stopping at about 2 gb.  If i remember right wasn't Fat32 limited to 2 GB partitions at sometime (or windows was?).  I'm just kinda thinking out loud here, but linux isn't stopping cause it expects the parition to be full is it?  

I also tried to copy to the other partition on my hard drive a Fat32 partition with 11+ GB free with same error.  Anything I can do?

---

### Post by John Nilsson on 2005-09-13
Assuming a cluster size of 16kb you'll have a possible over head of 120 000 * 16kb ~= 2gb but 2+2 is still not 16 though...

Is it possible that /tmp is involved in the transaction and thus the limit is on that fs?

---

### Post by dk_pa on 2005-09-13
I think that is the problem, honestly because I only have 5.5 GB free on my Linux partition (due to having these darn files ... hehe).  I broke some of it up into smaller directories.  I'll start with that and clear some space and go from there.  Thanx again.

---

### Post by Juergen on 2005-09-13
tar has options to create multivolume-archives.

I never needed it, but I think 'tar -L2000000 --backup=t -f...' or something like that might work. 

Read 'man tar' and 'info tar' for further info ;-)

---

