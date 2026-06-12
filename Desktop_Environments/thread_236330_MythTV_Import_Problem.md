---
title: "MythTV Import Problem"
date: 2006-08-14
forum: Desktop Environments
---

### Post by pipedream on 2006-08-14
I am able to play DVDs just fine in MythTV, I am using the recommended change to xine to play them.

When I go to import a VOB I am told “No jobs exist, Press 0 to import a DVD”.

I have properly selected one to all of the VOBs but continually get this message.

I do indeed have MTD running, so that is not the issue.

I created a directory as Mythtv to import to /Mythtv/store/ 

However, I can not seem to get it to work.  I have rebooted, tried multiple DVDs, but all to no avail.

Is there some other program a Mythtv user has to install for the “import” function to work or should it be “built in” to Mythtv?

I appreciate any help I can get on this issue.

I am a n00b so I apologize, but how do I know for sure if my Mythtv user has read/write rights to the directory that I created?

I use that same directory for buffering (Mythtv/store/buffering) and recordings (Mythtv/store/recordings) and it does just fine recording.

Thanks!

I have Ubuntu 6.06 and Mythtv 0.19 installed.

---

### Post by Diadem on 2007-03-06
I'm also a n00b at this stuff - I have been having this same problem. Originally my issue was the mythvideo directory didn\t exist - I did not know it needed changing, as it was not shown on the mythtv Howto on the community pages (which is what I have been using to set up mythtv). After i changed the directory, mytharchive almost worked once. It stopped a couple of minutes into the process. I checked the log at 

/var/lib/mythdvd/temp/mtd.log

and got this error:

Error: DVDPerfectThread could not open output file: /etc/mythtv/share/Movies/dvd/SHAOLIN SOCCER_001of
job failed: job dvd 2 3 -1 0 -1 /etc/mythtv/share/Movies/dvd/SHAOLIN SOCCER

I got an error when attempting to create an ISO as well. I am not sure if I have done something wrong with the directory again or if this is something else I have missed. 

I am running Edgy Eft with Mythtv .20

---

### Post by process91 on 2007-06-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/69651](https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/69651) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I got MythDVD to correctly Archive a DVD, and it's really sweet. Does a great job, takes about 4 hours on older hardware. I'm pretty experienced in getting that to work, so feel free to ask about how to burn a dvd. I also am trying to get the import function to work. I have gotten it to import correctly on ISO and Perfect after switching the directory and giving it write permissions, but I'm still trying to get it to work on Good, Medium, or Excellent. Here's what results in mtb.log -

19:06:28: Error: abandoned job because master control said we need to shut down
19:06:30: job failed: job dvd 1 1 3 1 -1 /media/sdb1/Media/History Of The World
19:11:29: a client socket has been closed
19:12:05: a client socket has been opened
19:24:22: Error: DVDPerfectThread read failed for 207 blocks at 1771644
19:24:35: job failed: job dvd 1 1 3 1 -1 /media/sdb1/Media/History Of The World Pt 1

If anyone has any ideas I'd love to hear them.

---

