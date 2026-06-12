---
title: "[SOLVED] showing combined system space"
date: 2009-01-05
forum: General Help
---

### Post by ffxigotenks on 2009-01-05
I have 4 hard drives ranging in sizes and they're all visable to my ubuntu system, my question is if there is a way to show total used and available space in a system, for example if I have 4 hard drives with 25GB used out of 100 GB total on each drive I want it to show me 100GB/400GB, if there's any way to do that so it will work with conky that would be even better. I have googled it and searched here and found nothing even close. thanks in advance

---

### Post by Ahadiel on 2009-01-05
I made this quick script in python that adds up the output from *df -h* and prints out usedGB/totalGB. It should be relatively easy to incorporate the output into conky.

[http://omploader.org/vMTNrYQ](http://omploader.org/vMTNrYQ)

---

### Post by jerome1232 on 2009-01-05
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

I don't know if you've looked over this thread but it's like 180 pages of .conkyrc scripts and screenshots there might be a config in there you like. You can always look at their .conkyrc and figure out how to integrate the relevant parts.

---

### Post by dcstar on 2009-01-05
> **ffxigotenks said:**
> I have 4 hard drives ranging in sizes and they're all visable to my ubuntu system, my question is if there is a way to show total used and available space in a system, for example if I have 4 hard drives with 25GB used out of 100 GB total on each drive I want it to show me 100GB/400GB, if there's any way to do that so it will work with conky that would be even better. I have googled it and searched here and found nothing even close. thanks in advance

The following is a script called** dfspace** (which I used to find handy when I used SCO Unix) which I found at:

[http://www.cygwin.com/ml/cygwin/1998-10/msg00170.html](http://www.cygwin.com/ml/cygwin/1998-10/msg00170.html)

```
#!/bin/sh -

# dfspace - d(isk) f(ree) space
#
# Calculate available disk space in all mounted filesystems
# with the exception of psuedo file systems such as /proc and /dev/fd.
#
# Alternately, report on filesystems/devices specified on cmd-line.
#   Filesystem may be 1K bytes/block, but, df uses 512 bytes/block.
#

# get free and allocated space.
df -k $* 2>/dev/null | awk '
BEGIN {  AVAIL=0; TOTAL=0 }
{
	if ( $6 != "/proc" && $6 != "/dev/fd" && $1 != "Filesystem" )
	{
#print $1 $2 $3 $4 $5 $6
		AVAIL += $4
		TOTAL += $2
		while (length($6)<28) $6 = $6 " "
		printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",$6, $4 / 1024, $2 / 1024, $4 * 100 / $2 )

	}
}
END { printf("-------------------------------------------------------------------------------\n")
printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",
	"            Total           ", AVAIL / 1024, TOTAL / 1024, AVAIL * 100 / TOTAL)

}'

# end of disk space calculation.
```

You can probably modify it to just display the last line.

---

### Post by ffxigotenks on 2009-01-05
dcstar, how do you run that script, is that perl? I've tried making it executable.. but I get nothing...

---

### Post by Ahadiel on 2009-01-05
> **ffxigotenks said:**
> dcstar, how do you run that script, is that perl? I've tried making it executable.. but I get nothing...
It's not perl.
[quote="dcstar"]#!/bin/sh[/quote]

---

### Post by ffxigotenks on 2009-01-05
<headdesk> leave it to me to miss the obvious.. perl starts with #/bin/perl >.< anyway, should "sh dfspace" work in this case? cause I'm just getting nothing, not even an error

---

### Post by ffxigotenks on 2009-01-05
ahadiel I've tried your script and it's reporting fine, except it's adding space from udev and tmpfs which wouldn't bother me, except tose folders are listed in megabytes and throwing the numbers off by 2K...

---

### Post by ffxigotenks on 2009-01-06
ok, I almost got it, I just needed to change the grep dev to grep dev/sd I'll play around with it some more later

---

### Post by ffxigotenks on 2009-01-06
ok, got conky to show the total space on my system using ahdiel's script, now, I may be getting a bit greedy, but I'm gonna hope against hope that there's an answer... is there a way for me to have a bar graph for this result in conky , currently I have 413GB/551GB showing, can conky calculate this and show it in a bar graph, just thought it'd be nice, but not necessary:D

---

### Post by ffxigotenks on 2009-01-06
I modified Ahadiel's python script (many thanks on that) and now I've figured out how to get it to show the total space, my only problem is that I don't know python so I'm not sure how to divide numbers... it now shows 482GB/701GB and I want to make it so it gives 69, thanks for all of your help

---

### Post by ffxigotenks on 2009-01-06
ok, I got it after a bit of trial and error, it works now :-D

---

