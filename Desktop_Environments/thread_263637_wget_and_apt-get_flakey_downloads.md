---
title: "wget and apt-get flakey downloads"
date: 2006-09-23
forum: Desktop Environments
---

### Post by mrashley on 2006-09-23
Since I have freshly installed 6.06.01 onto an AMD 1200+ with 768 megs of ram I have had a few problems that are possibly related.

Problem one:

If I wget a file - especially flash from the adobe website - it starts downloading, and then (I can only describe it as) it looks like it gets tired, stalls, resumes downloading for a few more seconds and finally stops. Wget eventually tries to resume the file tranfer once more, but the same problem happens. I can get the whole file by doing this over and over and over and over and over and (you get the point) but I shouldn't have to.

Problem two:

If I want to apt-get install something (same with synaptic) if the file is larger then part way through downloading it the file will slowdown and eventually stop downloading (again, as if the program has a cardio problem..)

Problem three:
(most likely unrelated, but just in case)
I can't look at many websites with firefox. Websites such as ubuntuforums.org. If I load them firefox just disappears. I tried loading from the command line and I get "Bus error" as the only exit signal.

I install swiftfox to be similar but different, and that worked for a while but now it doesn't even load. The error out is more significant but still not much.

```
/opt/swiftfox/run-mozilla.sh: line 131: 17468 Bus error                     "$prog" ${l+"$@"}
```

It's a fresh install for a new ubuntu user. I'm really sad that it's working out this way, because my laptop and ubuntu are such good friends.

---

