---
title: "kio_audiocd troubles"
date: 2006-03-09
forum: Desktop Environments
---

### Post by drx on 2006-03-09
I upgraded to KDE 3.5 from the packages at Kubuntu.org.

I remember a long time ago, when i put an audio cd into the drive, i got a great konqueror window showing me pseudo directories and files (mp3, ogg, wav) that i could just copy to my harddrive and the ripping would start. Now i should do that with kaudiocreator as it seems.

But this software (and also a konqueror-view on the cd drive) spawns a kio_audiocd process that takes more and more memory, until the computer finally hangs. -- I had to log in from another computer and kill the process on the console.

Is there any way to get this working again?

---

### Post by Shanachie on 2006-06-24
I have the same problem. I have confirmed [this]("https://launchpad.net/distros/ubuntu/+source/kdemultimedia/+bug/48731") bug, I suggest you do the same.
The bug reporter mentioned that he has a SATA DVD drive, like I do, so I guess that's what's causing it. Do you have a SATA drive to?

---

