---
title: "Auto MOUNT a CD drive in headless 8.04? Any Help :)"
date: 2009-05-15
forum: General Help
---

### Post by Dean Rotherham on 2009-05-15
Hi there Ubuntu users :)

I'm turning to this forum after a somewhat frustrating situation and good few days with no luck of how to do this :( .. In short I have a "headless" 8.04 Ubuntu system that I need to auto mount and run a script when inserting a CD (The script can be either on the CD or within the file system). I say "headless" as it's NOT the server version, but using the tool rcconf I turn the "gdm" component off and ALL activity on the machine is done WITHOUT a user logging in.

I understand the autorun.sh file on the CD component, but this seemingly only works when gdm is enabled (even then I still get a "popup" asking do I want to run the "autorun.sh", however this I'm not too worried about as ultimately I'm NOT using GUI) .. When not running the GUI (gdm) the CD is NOT even mounted automatically.

So how can I:

Auto Mount a CD in "headless" environment? (The sytem sits at the login terminal, so no usr is even logged in)

Auto Run a script either on the CD after mounting OR?

When a CD is mounted Run a script on the file system?

I REALLY hope this isn't too far off from topic to be addressed and I'll appreciate any help and guidance towards this. I am fairly new to Linux, but slowly finding my way round. So far I've looked at udev rules and think that could be the way to go, but not 100% sure.

Thank You in advance.

Cheers
Dean :)

---

### Post by KhurramM on 2009-05-15
I am not sure u can use bash

If yes, then grep out the output of the cat /proc/partitions

if it is true,

use the mount command

All above can be put in a script, run by cron every 10 seconds perhaps.

Hope this helps u...

---

### Post by Dean Rotherham on 2009-05-16
Heyo :)

Great Idea ... Tahnk You!!!! I'v ebeen think how this will work well .. BUT now having an issue with mounting the drive? The first part of my script is:


> DRIVE=/dev/scd0/
CD=/media/cdrom0/
ARCHIVE=$(ls $CD)
ALOG=/home/snb/Desktop/archive.log

#       (

mount $DRIVE

if fgrep -q $ARCHIVE $ALOG;then

echo ALREADY PROCESSED $ARCHIVE
umount $CD

else

And this seems to hang :( .. It's a littl eweird, if I run this a second timeit then work? Almost as if it "hanging" after mounting the cdrom. Do you know the correct way to mount a drive from a script?

Again thanks for you help :)

Chat soon
Regards
Dean

---

