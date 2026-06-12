---
title: "rhythmbox hangs when writing cd"
date: 2007-10-11
forum: Desktop Environments
---

### Post by jaybee99 on 2007-10-11
When I right-click on a playlist in rhythmbox and choose "Create Audio CD" everything goes OK until it gets to "Closing Disk". Then the app hangs altogether and when I finally kill it and eject the CD, it's not playable. Writing with k3b works fine. Any ideas?

This is using Edgy and rhythmbox 0.9.6.

Thanks,

---

### Post by safaricity on 2007-10-11
you know rhythmbox defaults cd-writing to serpentine?
me personally never had use for serpentine, so i purged it in usual.
but now i figure that you just need it installed for rhythmbox to burn cd´s. 
i do think there might be a gconf setting for this, where you eventually edit the chosen writing-tool...
just wanted to know it the prob is because of serpentine not installed

---

### Post by jaybee99 on 2007-10-12
I didn't know that -- thanks very much. Serpentine isn't installed so I'll install and have another go.

---

### Post by jaybee99 on 2007-10-12
Still doesn't work! Exactly the same thing happens. I'll start it from a terminal and see if there are any clues (which means wasting more blank cds!).

---

### Post by jaybee99 on 2007-10-12
Here's what I get in a terminal:

```

#lots of lines like this:
cdrecord stdout: Track 06:  117 of  129 MB written (fifo 100%) [buf  9cdrecord stdout: Track 06:  118 of  129 MB written (fifo 100%) [buf  9
cdrecord stdout: Track 06:  119 of  129 MB written (fifo  94%) [buf 10
cdrecord stdout: Track 06:  120 of  129 MB written (fifo  87%) [buf 10
#....
cdrecord stdout: Track 14: Total bytes read/written: 37429732/37432080 (15915 sectors).
cdrecord stdout: Writing  time:  266.593s
cdrecord stdout: Average write speed  16.4x.
cdrecord stdout: Min drive buffer fill was 41%
cdrecord stdout: Fixating...
cdrecord stdout: Fixating time:   13.130s
process stdout: HUP
cdrecord stderr: cdrecord: fifo had 11791 puts and 11791 gets.
cdrecord stderr: cdrecord: fifo was 0 times empty and 4718 times full, min fill was 76%.
process stderr: HUP

```
do you know what **process stderr: HUP** is about?

Thanks,

---

