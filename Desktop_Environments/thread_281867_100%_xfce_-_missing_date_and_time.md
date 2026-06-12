---
title: "100% xfce - missing date and time?"
date: 2006-10-21
forum: Desktop Environments
---

### Post by TiredBird on 2006-10-21
I went 100% xfce by running the script on [this page]("http://www.psychocats.net/ubuntu/purexfce") I'm beginning to think I made a mistake. Since doing so I have not been able to find a lot of the apps I was previously using. The latest is the date and time setting program. I seem to have lost it. Does anyone have any suggestions about what I should be doing now to set the date and time correctly.

---

### Post by fritz_monroe on 2006-10-21
Use the CLI.  [Here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugtime.html") is a page that gives some steps to set the date and time.  Basically to set the time, you do this.

```
$ date -s 10:10

$ clock -w
```

The first line sets the time.  The second puts it to the BIOS so it sticks.

---

### Post by TiredBird on 2006-10-22
Thanks for the help. I was using ntp to set my time. Can I do that with the commands you refer to?

---

### Post by TiredBird on 2006-10-22
I've looked at the man pages for the 'date' and 'clock' commands and can't find any reference to 'ntp'. I had 'ntp' working. Now it seems to be gone or at least I can't find it. Any suggestions for getting it working again?

---

### Post by fritz_monroe on 2006-11-10
Nope, the date and clock doesn't have anything to do with ntp.  But take a look at [this page]("http://www.eecis.udel.edu/~mills/ntp/html/ntpd.html") and [this one]("http://www.akadia.com/services/ntp_synchronize.html").  They explain a lot about ntp.  There's also [ntpdate]("http://www.eecis.udel.edu/~mills/ntp/html/ntpdate.html") that you can install via Synaptic.

---

### Post by rfruth on 2006-11-10
App > system > Time & Date ? 

[ATTACH]19151[/ATTACH]

---

