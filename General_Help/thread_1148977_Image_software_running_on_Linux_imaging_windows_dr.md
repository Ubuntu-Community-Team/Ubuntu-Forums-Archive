---
title: "Image software running on Linux imaging windows drive."
date: 2009-05-04
forum: General Help
---

### Post by trendal.toews on 2009-05-04
Is it available?  I have spent the last couple weeks on and off searching the web for an alternative to Acronis that will run on Linux.  I'm afraid I am using the wrong search words or something either that or it doesn't exist.

I image windows drives daily with Acronis on windows but sometimes a windows box won't see the drive because it is physically damaged.  Often in this case a Linux box will read the files which is nice because you just do a fresh install and transfer the data and your good to go.  But I would like to image the whole drive from Linux like I can do in windows with Acronis.  It saves a lot of time for me and the customer rather than installing all the programs and what not.

Note:  I am not trying to image Linux drives, at this point anyway, just windows drives from Linux.

Thanks

---

### Post by gmrishel on 2009-05-04
I have used dd in the past for issues like this.  Even been able to rescue a RH install that had a bad hard drive by imaging it to a new drive.  Be careful with it, do things wrong and as far as I know, the drive is unrecoverable.

---

### Post by trendal.toews on 2009-05-04
dd.....?  Okayyyyyy,  I will search on that.  Not trying to get something without any effort on my part but I got to admit I haven't heard of dd before.8-[

---

### Post by trendal.toews on 2009-05-05
Found a really informative article [here]("http://www.forensicfocus.com/linux-dd-basics") that got me going on the right track.  Now I am trying to clone a 40GB drive to a new drive using the knoppix 6 CD.  I used the noerror,sync switches because the if drive is physically corrupted and would just error and stop otherwise.  The main problem I see is time.  It has been running for over 2 hours and is showing 12 GB copied.:-&  Oh well.  Windows just crashes if you try to read the drive so an extended copy time is better than lost data.  But the amount of errors that I am seeing is got me wandering if it ain't gonna be a repairable/bootable drive when I am done.  Oh well, experience I guess. At least Linux is trying to make an image, windows just falls on its nose without putting forth any effort.

---

