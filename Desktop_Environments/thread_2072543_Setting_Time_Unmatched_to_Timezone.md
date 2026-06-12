---
title: "Setting Time Unmatched to Timezone"
date: 2012-10-18
forum: Desktop Environments
---

### Post by jakfish on 2012-10-18
Running Lubuntu 12.04 on Lenovo S10-3t netvertible and within /etc/default/rcS, I've set it "UTC=no"

The rub is, I do a lot of timezone traveling and in Google Calendar, I need to have a timezone that doesn't use daylight savings.  So I use Bogota, Columbia timezone (GMT +5).  But I set my clocks to local time here in Athens, Greece.

This approach works with Google, Windows 7, Puppy Linux, and other Linux OSs, but not with Lubuntu.

Even though the correct BIOS time shows up in Lubuntu upon boot, Lubuntu eventually changes time to actual time in GMT +5.

Other than sudo-ing a time change in console after every reboot (or suspend), can I stop this automatic time change?

Many thanks for any suggestion,
Jake

---

### Post by jakfish on 2012-10-21
Answering my own post, having a clock set to anything different the established timezone can't be done in Lubutu.  Unless it's done manually upon reboot, Lubuntu will simply reset BIOS clock to said timezone, which is  odd, since other Linuxes will bow to your choice.

My problem was with Google Calendar/Rainlendar, and for this, the solution is to cave in and set the timezone of your actual location, then go into Rainlendar/Options, and set "Time offset (mins)" to correlate with local time.  That way, Rainlendar will sync properly and you don't need to mess with specs in Google Calendar.

An arcane problem and solution to be sure, but perhaps some lost soul with the same problem specs will stumble across this.

All is well now, timezone-wise, and Lubuntu 12.04 impresses me more and more, now that I know what time it is.

Jake

---

