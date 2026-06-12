---
title: "Backup questions (rsync -Cavz and diff -rq)"
date: 2006-09-21
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-09-21
Some background info (how I do my backups):
```
rsync -Cavz /dest /target/ # to copy my stuff from hard disk to removable hard drive
diff -rq /target /source | less # to check if I copied everything (files with some weird characters will stay behind)
```

and my questions are:
rsync: 
* assume I did my rsync command (rsync -Cavz /dest /target/) and now I have dest under target. If I do it again in fifteen days, will it copy over files that already exist but I changed? I read the man but I couldn't quite get it... 
* Are there any downsides to this? 

diff: 
* suppose file a.odt and b.odt exist both under source and target. but they are different (for example: I added a word inside the text file a.odt). will diff pick that up? I know it "compares files line by line", but in what meaning? 

Basically, I am trying to make sure I can do my backups without transfering 30GB of data from local hard disk to removable hard disk every 15 days :)

Any help, pointers, practical advice, anything is really appreciated :) thanks :KS

---

### Post by aysiu on 2006-09-21
As long as you use exactly the same command every time, it will copy only new or modified files. I'm not sure what the -C and -z options do. I just use ```
rsync -av /original /target
```

---

### Post by towsonu2003 on 2006-09-21
I found the options from a web site. from the man page, z compresses data during the transfer (less data means faster process I guess?). For C, it says "auto-ignore files in the same way CVS does", which I thought was something good... 

I don't remember which website it was

---

### Post by aysiu on 2006-09-21
Actually, I'd think quite the opposite--that it would take a little bit longer to compress everything, but it would take up less space (presumably the advantage of compression).

I don't know what "the way CVS does" means. All I know is that *-av* works just fine for me.

---

### Post by towsonu2003 on 2006-09-21
thanks, I'll go with -av as well :)

so rsync -av won't miss anything.

any thoughts about diff -rq? does it miss anything?

---

### Post by aysiu on 2006-09-21
I've never used *diff* before.

People give me a lot of recommendations with explanations in [this thread](http://ubuntuforums.org/showthread.php?t=209724), though.

---

### Post by jameso on 2006-10-10
I have been told to only use the -z option when transferring over a slow network. All -z does is compress the data **during** transfer, which is typically useful over a slow network connection.

If rsyncing files from one partition/drive to another (ie not over a slow network connection), it is faster to not use the -z option. This is because you don't waste memory and cpu time compressing and uncompressing the data.

---

### Post by towsonu2003 on 2006-10-10
> **aysiu said:**
> I've never used *diff* before.

People give me a lot of recommendations with explanations in [this thread](http://ubuntuforums.org/showthread.php?t=209724), though.
replying a little late :) I guess the forums forgot to send me a notification -does that from time to time-

now I know why rsync doesn't sync nicely with fat32 :)
> **jameso said:**
> I have been told to only use the -z option when transferring over a slow network. All -z does is compress the data **during** transfer, which is typically useful over a slow network connection.

If rsyncing files from one partition/drive to another (ie not over a slow network connection), it is faster to not use the -z option. This is because you don't waste memory and cpu time compressing and uncompressing the data.

thanks. I'm no longer using the -C option. that's what happens (comsume cpu for nothing) when you don't read the man page of a cli command while reading a howto :)

I'm still waiting for thoughts on diff, though, if there are any. or may be I should your md5sum to check if all the files are copied over, but I am guessing that would take too long and consume too much cpu. you have to first get md5sums fo all files you got in local hard drive, than get md5sums of all files on the back up location, than compare them... and doing this every month would kill me :)

even diff takes ~20 minutes for 15G of data compared between a fat32 external [enclosure] hard drive and the local hard drive...

---

### Post by jameso on 2006-10-11
I am not sure about verifying that each file has transferred correctly. 

Does anyone else have any ideas on the best way to do this?

---

