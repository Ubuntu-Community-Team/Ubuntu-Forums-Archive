---
title: "Kubuntu Handbrake not reading disk"
date: 2006-10-12
forum: Desktop Environments
---

### Post by andcraig on 2006-10-12
I'm running kubuntu and attempting to use Handbrake. I got it to compile and running the executable works, but it fails to read the DVD's. 
I've tried with iso files that are mounted, the dvd drive, and multiple isos and dvd disks.

the verbose output i get is
```
andrew@andrew-desktop:~/handbrake$ handbrake -v  -e x264 -E faac -2 -w 512 -i /media/hdc -o /home/andrew/slevin.mp4
[11:34:59] hb_init: checking cpu count
[11:34:59] hb_init: starting libhb thread
[11:34:59] thread -1211065424 started ("libhb")
HandBrake 0.7.1 (2006022400) - http://handbrake.m0k.org/
1 CPU detected
Opening /media/hdc...
[11:34:59] hb_scan: path=/media/hdc, title_index=1
[11:34:59] thread -1219458128 started ("scan")
[11:34:59] scan: trying to open with libdvdread
[11:34:59] dvd: DVDOpen failed (/media/hdc)
[11:34:59] scan: trying to open as VOB file
[11:34:59] scan: fopen failed
[11:34:59] thread -1219458128 exited ("scan")
[11:35:00] thread -1219458128 joined ("scan")
[11:35:00] libhb: scan thread found 0 valid title(s)
No title found.
[11:35:00] thread -1211065424 exited ("libhb")
[11:35:00] thread -1211065424 joined ("libhb")
HandBrake has exited.

```

Has anyone encountered this before or have an idea on how to fix it?

---

