---
title: "Deadlock combined with read-only filesystem."
date: 2009-06-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jdacronym on 2009-06-02
I upgraded to Hardy about five days or so after LTS ended on Gutsy, which had been working fine (so good that I went for almost 200 days without rebooting).

However, since my upgrade I've been having a strange problem; my computer will occasionally deadlock, and my filesystem becomes read only, leading to a lot of:

$ ls .
bash: /usr/bin/ls - input/output error

...or it seems that a read-only file system is the problem.  Some threads I've read say this is a last-ditch effort of the system to protect the filesystem or hard-drive from damage.  I've run smartctl -H and smartctl --all against my hard drive, and it passes, so I'm thinking it's not the hardware.

The main symptom is that my CPU and Disk usage monitors suddenly shoot up to 100%.  I generally have top open in a terminal when working, and I noticed that klogd, dd, and ksoftirqd were usually the top CPU users (along with either firefox or evince -- usually firefox).  Up until now I was unaware of these programs (though I'd read in the Jargon File that dd is a holdover from IBS System/360 or something).

I've submitted a bug report on this <https://bugs.launchpad.net/ubuntu/+bug/368324>, after originally posting about my problem in <https://bugs.launchpad.net/ubuntu/+bug/249123>, which now appears to be a different issue.  You can read about my trials there in detail if you're so inclined.

The read only filesystem problem happened by itself recently, and also a few days ago Xorg choked and died without warning.  I copied a few log files after reboot, but I don't know if it has any useful information.

The latest occurence (today) was particularly dramatic.  Firefox 3 started thrashing (I have a dual core machine, and I could see it skipping from one CPU to the other on my system monitor).  My system slowed to a crawl but I managed to get an open terminal to respond and killed it. I thought I was safe, but then this old deadlock problem happened again, for the n-th time.

Usually, I can still run whatever terminal programs I'd already run that session, as they're still paged into memory.  However I couldn't get dmesg to run.  So much for that.

However, when I rebooted I immediately made copies of Xorg.*, dmesg*, messages, kern.*log and syslog* from /var/log.  I noticed that /var/crash is empty, though, which isn't always true, but I don't know what that means.

I've been hoping that I could get some help by posting the bugreport on launchpad, but aside from one user (Rob), I haven't had much in the way of responses.  I'm hoping this will work out better.

Let me know which of my logfiles you need me to post, if any.

~jdacronym

---

### Post by jdacronym on 2009-06-05
Well, this problem has recurred, but I tried something different this time that may shed light on the situation.  I am beginning to think that Firefox 3 may be part of the problem, though the problem seems to do with ACPI.

I unplugged my laptop at the end of a day at work, and suddenly, just like the last time this happened, my system started thrashing.  I couldn't get to a terminal running `top' but the last time this happened, firefox was the offending process.

To try something different, I plugged the AC power back in, and the thrashing stopped.  I'm not 100% sure it stopped thrashing because I plugged back in, but it seems a pretty compelling coincidence.

But the damage was already done.  My filesystem was apparently now read-only, and I got input/output errors from bash when I tried to run df, dmesg, ls, or other programs that I hadn't run recently.

Hopefully somebody can help me,
~jdacronym

---

### Post by jdacronym on 2009-06-08
Bump!

I just updated the bug-report at [https://bugs.launchpad.net/ubuntu/+bug/368324](https://bugs.launchpad.net/ubuntu/+bug/368324) with some more error messages I copied by hand from dmesg this latest time it happened.  My other logs seem to simply jump from the time my filesystem went read-only to when I restarted, so no help there.

---

