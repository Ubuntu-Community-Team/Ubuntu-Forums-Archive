---
title: "Linux alternatives to Lab View for audio sampling?"
date: 2010-07-06
forum: Education &amp; Science
---

### Post by wannabegeek on 2010-07-06
hi,

I am involved in a project which uses a hydro-phone installed on a pier in
San Francisco Bay, which is used to record the migratory Toad Fish aka Midshipman.

The males hum at 100 Hz and frequency is strongly temperature dependant.
We use Lab View to sample 15 minute chunks of data from the hydro-phone 24/7
and upload this data to other machines running CentOS.

In case you are wondering, the signal from hydro-phone has a built in FET pre-amp then  comes into a home made phantom power  amp which also sends the signal up to the capture machine. The signal comes through a differential amp then to an anti-alias filter and finally to data aquisition card and then Lab View.

My understanding, is that the data aquisition cards are not well supported  outside of windoze. I am hoping to find a Linux program which can interface the aquisition card and produce the samples. I will update this thread with details on the card.

thanks for your help,
wbg

---

### Post by hubie on 2010-07-08
If you can't get your data acquisition card to work in linux, have you considered grabbing the data with a sound card?  There are a number of programs out there to do this.  Most of them are part of projects that use the sound card to make spectrum analyzers or oscilloscopes and they leverage the usual sound libraries.

---

