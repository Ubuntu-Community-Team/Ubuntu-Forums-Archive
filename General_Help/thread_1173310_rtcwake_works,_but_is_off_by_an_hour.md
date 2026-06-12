---
title: "rtcwake works, but is off by an hour"
date: 2009-05-29
forum: General Help
---

### Post by Altay_H on 2009-05-29
For some reason when I enter a time for rtcwake, it receives it differently. Let me demonstrate my problem:
```

$ date
Fri May 29 14:47:15 EDT 2009
$ date --date "Fri May 29 14:48:15 EDT 2009" +%s
1243622895
$ sudo rtcwake -l -t 1243622895 -m on
rtcwake: wakeup from "on" using /dev/rtc0 at Fri May 29 13:48:17 2009

^C
$ sudo killall rtcwake
rtcwake: no process killed
$ date
Fri May 29 14:48:17 EDT 2009
$ sudo rtcwake -l -t 1243622895 -m on
rtcwake: time doesn't go backward to Fri May 29 14:48:15 2009

```

You'll notice that the first time I set a time for rtcwake, it set it incorrectly. I told it to set a wakeup time for 14:48, but it set it for 13:48. The time that it actually wakes up is the time it returns, not the time I set.

The second time I tried to set it for the same time, but now the time was in the past rather than the future. rtcwake behaves correctly when the given time is invalid. It recognizes the time correctly.



Both my "date" and "hwclock" agree on the time, so it's not due to rtcwake reading the time from the wrong place.
```
$ date
Fri May 29 14:55:59 EDT 2009
$ sudo hwclock
Fri 29 May 2009 02:56:00 PM EDT  -0.486707 seconds

```

Also, I'm having this exact same issue on two computers running Ubuntu, so it's not specific to my hardware.

The only other thoughts I have are timezones and daylight savings time. I don't think it's either of these though, and I don't see how they could be involved. There's an obvious workaround, but I'm more interested in figuring out where the problem is coming from than workarounds. Thanks for any help.

---

### Post by Altay_H on 2009-08-21
Bump. I can no longer get rtcwake to wake up my computer from sleep and the time it reports is now off by a full five hours. Any ideas or information regarding rtcwake would be greatly appreciated.

---

