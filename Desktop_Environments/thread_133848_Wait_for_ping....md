---
title: "Wait for ping..."
date: 2006-02-20
forum: Desktop Environments
---

### Post by cheuschober on 2006-02-20
Hey everybody! (*waits for the obligatory 'Hey Dr. Nick!'*)

So I -know- I saw this in a post maybe a week or two ago when I had no idea whatsoever what it meant at the time but after spending the last half hour searching for the answer I thought I'd ask if anyone had any thoughts on my brief quandry:

I just created my first executable (what small joy!) It's a mounting script to first create directories in /mnt/ and then to mount 6 shares from a certain pair of servers whenever I join a particular network (ifup ath0=ath0-ChadWLan). There's a sister that unmounts at post-down.

Currently I call the executable in the post-up section of my interface but I run into the problem that the first share never gets mounted when triggered via ifup. If I execute it directly all's well--no problems.  I'm assuming because the post-up event fires before the connection is fully established or something to that extent. In any case what I'd like to do is create a wrapper for these create dir / mount commands that  throws 5 pings at the server (paced normally) and at the first response runs my mount commands--if none respond returns an error and doesn't run the mounts.

I openly admit I know -nothing- about the scripting engine of Linux but I'd like to learn (even something as simple as the linux equivalent of IF). Any help would be graciously accepted and greatly apreciated.

Regards,
~Chad

---

### Post by suRoot on 2006-02-21
Why not just tell the script to wait a few seconds for the interface to come up?

```
sleep 30
```

would make it wait 30 seconds before running any further commands.

---

