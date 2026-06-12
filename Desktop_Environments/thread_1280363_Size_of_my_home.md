---
title: "Size of my /home"
date: 2009-10-02
forum: Desktop Environments
---

### Post by jakerue on 2009-10-02
I have been having issues with my /home folder size.  

My df-h results in [http://paste.ubuntu.com/283483/](http://paste.ubuntu.com/283483/) ...this shows my sda6 as only 50% full

when I run the Disk Usage Analyzer my home is 100% used.  Where are my 25 gigs?  I cannot figure this out and it's driving me up the wall.

I used gparted to play with the size - I shrunk and enlarged followed by  fsck, resize2fs.  Rebooted, sudo apt clean and emptied the trash.  

Screenshot of the df -h and DUAnalyzer side by side
[IMG]http://www.postimage.org/Ts1psCDA.png[/IMG]

What am I doing wrong here?  I must be completely off in the wrong direction because I cannot figure this out....

Jason

---

### Post by yabbadabbadont on 2009-10-02
First off, /home on your system is just a directory in the root filesystem.  (as shown by your df -h output).  :)

Second, what is the output if you run "df -i" instead?  (It shows the inode usage)

---

### Post by jakerue on 2009-10-04
When I run df-i I get 

[http://paste.ubuntu.com/285767/](http://paste.ubuntu.com/285767/)

Not sure how to interpret that

---

### Post by yabbadabbadont on 2009-10-04
It means that you have plenty of inodes left free.  Is the only reason you made this thread because of what the Disk Usage Analyzer is showing?  I mean, you haven't had any trouble creating new files or saving downloads or anything have you?  If not, then it is probably just a bug in DUA and you should search launchpad to see if there is one open for it already.  If not, create a new one.

---

### Post by jakerue on 2009-10-04
I have had issues with my sync software Spideroak (which is having it's own issues).  It was having issues placing things in my Home folder so I checked the DUA and it said everything was full.

It just seems like no change I make has any effect on the DUA.  If I do have space but DUA says I don't then as long as it doesn't impact me then I'm fine.  Thanks for the help and if I have more issues I will be back.

Thanks again

---

### Post by renkinjutsu on 2009-10-04
clarification


the disk usage analyzer is correct... and what df is showing you is correct..

You probably clicked "scan home" or something..

say your /home/user folder is 100GB

and say your music folder is 20GB

your results would be 

[COLOR="Red"]/home/user 100%[/COLOR]
[COLOR="blue"]/home/user/music 20%
blah blah blah 10%
*and the rest add up to 100%*[/COLOR]

and likewise, if you clicked "scan filesystem"
and scroll down to home.. you will likely see a number around 66% or so.. (doing the math based on your screenshot.. no decimal places D; )

the DUA's output is based on total space USED and does not tell you anything about free space.. so a result like
[COLOR="Red"]/home/user 100%[/COLOR]
[COLOR="Blue"]/home/user/Videos 50%
/home/user/Music 50%[/COLOR]
is normal..

---

