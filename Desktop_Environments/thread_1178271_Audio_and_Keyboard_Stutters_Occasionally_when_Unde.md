---
title: "Audio and Keyboard Stutters Occasionally when Under Certain Loads"
date: 2009-06-04
forum: Desktop Environments
---

### Post by professorYaffle on 2009-06-04
Under certain loads my desktop "stutters". There are two distinct symptoms but I suspect they have the same cause as the occurr under the same conditions:

   1. Audio output disappears for about 5 seconds, and
   2. keyboard input hangs for about 5 seconds.

It's very ephemeral and hard to reproduce deliberately, but when it's happening it happens at worst, about once every minute or two. The audio dropout doesn't seem to interfere with the actual music player - it's essentially just muting the output for 5s - like playing "Pick Up Song" (I'm Sorry I Haven't a Clue). The keyboard situation is *much* more frustrating. The events get held up in a buffer somewhere and aren't lost, but for the 5s or so they're in waiting X goes on processing as normal. So if the blockage happens between the key down and up events you get 5s worth of auto repeating typing into whatever application you were using at the time. [***Really*** annoying if the key that appears to be stuck down is *delete* or *backspace*!]
Note: I don't think I've ever noticed the audio drop out at the same time as a key gets "stuck".

The "load" situation may be a bit non-standard. It's a quad core machine and has all 4 cores constantly running boinc (climateprediction.net) so it is *always* fully loaded but dosen't normally have any problems:

[FONT=Courier New]%boinc-client status
 * Status of BOINC core client: running.
 * Scheduling of BOINC core client:
PID 21843: PRIO   0, POLICY D: SCHED_IDLEPRIO, NICE  19, AFFINITY 0xf
 * Scheduling of BOINC core client's children:
PID  3193: PRIO   0, POLICY D: SCHED_IDLEPRIO, NICE  19, AFFINITY 0xf
PID  3194: PRIO   0, POLICY D: SCHED_IDLEPRIO, NICE  19, AFFINITY 0xf
PID  3197: PRIO   0, POLICY D: SCHED_IDLEPRIO, NICE  19, AFFINITY 0xf
PID  3198: PRIO   0, POLICY D: SCHED_IDLEPRIO, NICE  19, AFFINITY 0xf
[/FONT]
I'm using fluxbox for the desktop and I have that, X and a few apps like amarok and my xterms (but not the shells therein) running at nice -10. Synergy is also running and connects me to 2 other nearby machines.)

The problems start when I run a job that uses 100% CPU (1 core) for a while. E.g. running a debug version of some 3D modelling regression tests under valgrind. (nice = 0). The other 3 cores can be happily running nothing but boinc (nice 19 , idle priority) and I still get the occasional 5s audio/keyboard hangs (although sometimes it can go for half an hour or so fully loaded without me noticing any hiccoughs.) The machine  is pretty meaty - I can run regression tests variously using plenty of CPU &/or I/O parallelised 3 per core (12 jobs in parallel) all at nice 0 and still use the desktop fairly comfortably except for this stuttering.

The machine is a Dell Precision T3400 - but not one with Ubuntu supported by Dell. I ripped Windows Wasta off when it turned up and installed Ubuntu  8.04 LTS amd64 desktop from the alternative install CD (I've got the partitions striped across 2 disks using lvm). It's fully up to date (as of this morning) and running kernel "2.6.24-24-generic #1 SMP". It's got a Q9550 CPU and 8GiB RAM. Audio comes from onboard the motherboard:
[FONT=Courier New]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)[/FONT]
and works fine otherwise.

There's nothing in /var/log/messages when the hangups happen. I can't see anything obvious in the other log files wither. I don't know where to look to start diagnosing this problem. Does anybody have any ideas as to what to do next?

---

